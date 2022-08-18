## Proposed Stats

    item psi_armor //weights 220
    {
        name        "_Psi-Amp Armor"
        image       armor/medium
        model       soldiers/mmedium/body
    //  image       armor/psi
    //  model       soldiers/mpsi/body
        type        armor
        category    3
        shape       "0 0 3 4"
        center      "0 0 -5"
        scale       0.7
        price       23000
        buytype     3

        protection
        {
            normal  35
            blast   55
            fire    30
            shock   30
            laser   30
            plasma  55
            tachyon 20
            stun    35
        }
        hardness
        {
            normal  6
            blast   10
            fire    13
            shock   13
            laser   20
            plasma  4
            tachyon 100
            stun    100
        }
    }