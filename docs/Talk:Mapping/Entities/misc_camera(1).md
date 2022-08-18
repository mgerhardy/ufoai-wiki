- I love it :) --[ShipIt](User:ShipIt "wikilink") 16:13, 6 October 2012
  (SAST)
- The max detection range is 800 map units? Maybe this could be a
  property of the entity, so the mapper can adjust it if he needs to?
  --[ShipIt](User:ShipIt "wikilink") 16:13, 6 October 2012 (SAST)
  - Good idea - will implement it. --[Mattn](User:Mattn "wikilink")
    20:08, 6 October 2012 (SAST)
- Right now it seems the model is always placed right in the middle of
  the actual actor cell. In order to add this to existing maps we would
  need some more freedom to place it. This is especially true for the
  height (z-axis). --[ShipIt](User:ShipIt "wikilink") 16:13, 6 October
  2012 (SAST)
  - this is a problem with the box size in entities.ufo. Should indeed
    be fixed. --[Mattn](User:Mattn "wikilink") 20:08, 6 October 2012
    (SAST)
- The angles key is not working. This might be needed if somebody wants
  to choose a different, static model for the camera. Does this only
  require to be defined in entities.ufo?
  --[ShipIt](User:ShipIt "wikilink") 16:13, 6 October 2012 (SAST)
  - Angle key is not working because the camera is implemented as 360°
    viewangle. It shouldn't be that hard to implement a frustom view for
    it though. --[Mattn](User:Mattn "wikilink") 20:08, 6 October 2012
    (SAST)
- As proposed by [H-Hour](User:H-hour "wikilink"), having an option to
  switch the cameras on/off (maybe by placing an actor at a certain
  point of the map) would be great. One way to display this to the
  player I could think of would look the same way as the Rescue zone
  button. No button means no cameras available, Button greyed out means
  cameras available but not activ, button shines if cameras activated.
  --[ShipIt](User:ShipIt "wikilink") 13:09, 8 October 2012 (SAST)
  - I would more vote for the generic user interaction highlighting like
    for the doors. We already have it, and in combination with the
    trigger_touch, this feature is very easy to implement.
    --[Mattn](User:Mattn "wikilink") 15:35, 8 October 2012 (SAST)
    - I am fine this way, too. But not sure about the feedback for the
      player. How can we tell him whether the cameras are on or off in
      this case? --[ShipIt](User:ShipIt "wikilink") 15:39, 8 October
      2012 (SAST)
      - Is it possible to have an icon hover over the head of a soldier?
        This could indicate that the soldier is "monitoring the
        cameras". We would also need some way to highlight or indicate
        WHERE THE CAMERAS ARE that he's watching. I will try to draft up
        an image if I can find the time.
        --[H-hour](User:H-hour "wikilink") 00:05, 9 October 2012 (SAST)
        - Just wait some days until I'm done with the stuff we already
          have. Then we can talk about how to improve it.
          --[Mattn](User:Mattn "wikilink") 08:16, 9 October 2012 (SAST)