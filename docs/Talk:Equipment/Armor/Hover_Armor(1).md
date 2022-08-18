## Proposed Stats

    item hover_armor //weights 260
    {
        name        "_Hover Armor"
        image       armor/medium
        model       soldiers/mmedium/body
    //  image       armor/hover
    //  model       soldiers/mhover/body
        type        armor
        category    3
        shape       "0 0 3 4"
        center      "0 0 -5"
        scale       0.7
        price       27000
        buytype     3

        protection
        {
            normal  45
            blast   65
            fire    75
            shock   30
            laser   30
            plasma  65
            tachyon 25
            stun    97
        }
        hardness
        {
            normal  12
            blast   20
            fire    20
            shock   20
            laser   32
            plasma  4
            tachyon 100
            stun    100
        }
    }