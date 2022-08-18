##  Remove node casting

Node casting like:

    *node:(abstractnode)foo.bar

Is a bad thing for scripter. It is only a usefull thing for parsing, but
we can't ask scripter to think as a parser. With a runtime cache, we may
remove that node casting.

Note: We use the casting to convert string value of affectation to
binary data (according to the typed node). Biggest problem is to do it
at runtime, and speed up it with some cache.

When it is done, we can work around to clean up the code, and cache some
data to speed up the computation. But ATM there is no slow down, cause
the previous code do not use any trick.

##  Use "(" and ")" and "," as real token

Writing:

        if ( "foo" ne "foo2" ) { ... }

is horrible.

With some work, and if we remove the casting syntax, we can write the
more common:

        if ("foo" ne "foo2") { ... }
        call *node:fooo("aaaa", "bbbb", "cccc", "dddd")

## Var

Supporting local var and removing "injection". Here we use GLSL-like
cast (C++-like constructor ), both look and feel and parsing is easier
than the C-like casting. `this` and `root` and `parent` are reserved
token var identifying know nodes.

    func foo {
        cvar a = cvar("sv_foo")
        node b = this.parent
        node c = root
        node d = node("root.foo.bar")
        node e = node("root." + d@name + ".foo.bar")

        d@color = "0.6 1.0 0.0"
        ...
    }

### What syntax to check if a cvar exists?

    // problem is this syntax will create the cvar, then it exists
    cvar a = cvar("sv_foo")

    // possible way to only get a cvar, without creation,
    // it allow to test the <code>a</code> var with an exists operator.
    cvar a = getcvar("sv_foo")

### What syntax to affect a cvar to a var (reference)?

    cvar a = cvar("sv_foo")
    // what should it mean?
    // 1) we set the value of <code>sv_foo2</code> to a (then to sv_foo</code>),
    // 2) we link <code>a</code> to <code>sv_foo2</code>, then no value change else <code>a</code> reference
    a = cvar("sv_foo2")

    // a) one solution to force using value (hmmmm not sure ATM this operator do a concatenation of string)
    a = "" + cvar("sv_foo2")

    // b) same as a) in this case both are possible
    a = string(cvar("sv_foo2"))

    // c) another solution to force using value
    a@value = cvar("sv_foo2")

    // d) another way to manage cvar?

This problem also exists when we want to assign a cvar to a node
property. The syntax must work for both var or node property. <node> //
? this.spinner.@current = string(cvar("sv_foo2")) // ?
this.spinner.@current = cvar("sv_foo2") </node>

### Reference problem (not syntax problem but architecture)

We use reference instead of requesting everytime thing by name. Idea of
var is to have something readable and faster. It is not hard to use name
instead of ref, but it will lose all the power of the feature. A script
must be safe, and must not segfault.

There is no cvar listener for destruction. If we assume we store cvar
name, there is no problem, and the cost should not be too much.

    cvar a = cvar("sv_foo2")
    cvar b = cvar("sv_foo2")
    delete b // it delete the cvar
    a = 4 // segfault...

There is no node listener for destruction. If we assume we store node
path, there is no problem, but the cost will be bigger, cause we must
parse the path every time we access to a property.

    node a = this@createchild("spinner", "fooo")
    node b = this.fooo
    delete b // it delete the dynamic node
    a@max = 10 // segfault...

With listener, we can fix all the var stack without problem. Slower, but
safe.

## More type

        string a = "aaaaa"
        float b = 1.3
        int c = 1

## Param

When "injection" is no more need, we can use named param.

###  Level 1

Transition can be done with reserved token var `param1`, `param2`,
`param3`...

### Level 2

    func foo {
        param ( a , b , c , d )
        ...
    }

Or moving it on the node parsing, if possible

    func foo ( a , b , c , d ) {
        ...
    }

### Level 3

And type it, if possible

    func foo ( string a , int b , float c , int d ) {
        ...
    }