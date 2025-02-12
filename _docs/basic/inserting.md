---
title: Inserting
description: Inserting operations in mei-friend
permalink: /docs/basic/inserting/
layout: page
---

# Inserting in the editor and notation panel

There are two ways to insert elements into your MEI-file: Either writing by hand directly in the editor panel or by using `Insert` (or rather the corresponding [keyboard shortcuts]({{ site.baseurl }}/cheatsheet){:target="_blank"}) in the notation panel.

Using the editor panel you can simply edit the encoding, changing attribute values or adding new elements. Typical text editing functions are available that you can find under [Edit]({{ site.baseurl }}/docs/basic/editing) in the menu bar like "Undo", "Search" or "Replace".

Adding new elements by hand is tideous though and generally not recommended. Using the `Insert` menu in the menu bar (or shortcuts) to add elements is generally the better way or just copy already existing elements. If you copy elements be mindful to change the `@xml:id` so there aren't multiple elements with the same `@xml:id`.

If you edit directly in the notation panel you can also select multiple elements and make changes for more than one at once. To make it easier to select slurs or difficult to click articulations like staccato dots or accents you can enable [drag select]({{ site.baseurl }}/docs/basic/settings/#drag-select): Go to `settings -> mei-friend` and enable `select slurs` and `select placement elements` under `drag select`. Holding "Ctrl" and leftclicking to select multiple elements is also possible. To select a chord hold "Alt" and click a note from the chord.

<figure class="figure">
    <div class="figure-title">Fig.&thinsp;1: Drag select.</div>
        <img class="figure-img" src="{{ site.baseurl }}/assets/img/inserting/drag_select.gif" 
            alt="Drag select." />
    <figcaption class="figure-caption">To be able to select slurs and placement elements, drag select has to be enabled for these elements.</figcaption>
</figure>

{% include alert.html type="info" title="Select approporiate elements" content="Make sure that you select appropriate elements, i.e. if you select an entire measure you won't be able to insert any elements, but you will still be able to shift the pitches of all selected notes." %}

## Inserting elements

### Inserting articulation

Articulation can be added by selecting a single note but also by selecting multiple notes and adding the same articulation for all of them. Select multiple notes either by drag select or by using holding "Ctrl" and leftclicking all the desired notes.

### Inserting spanning elements

To add spanning elements like a slur select the starting and ending note (notes between can also be selected, the element will be added from first to last selected) and either use `Insert -> Slur` or simply use the hotkey "s". This will add a slur above the notes selected. With "Ctrl + s" it can be added below. If only one note is selected the element will use the next note as the endpoint. The `<slur>` element can then also be found in the encoding and edited here if necessary. You might want to add the attribute `@place=below` manually or just use "X" with the slur selected.

**insert gif adding a slur and inverting placement**

Spanning elements added this way will always have a `@startid` and `@endid` which reference the `@xml:id`'s of the starting and ending note. Equivalent to this a spanning element can also be sufficiently defined by specifying the `@staff` and two timestamps `@tstamp` and `@tstamp2`. This method is commonly used for hairpins.

These two methods can also be mixed by using `@startid` with `@tstamp2` or `@tstamp` and `@endid`. You can use this method if a slur has a starting note but doesn't have a ending note. A classic situation would be at repeats or multiple endings (as seen in the Fig. 1). This method does not have to be used over page or system breaks! Just specify the start and end point and it will be rendered correctly.

<figure class="thirdwidth">
    <div class="figure-title">Fig.&thinsp;2: Slurs with no specified ending/starting point.</div>
        <img class="figure-img" src="{{ site.baseurl }}/assets/img/inserting/spanning.PNG" 
            alt="Screenshot of slurs with no specified ending/starting point" />
    <figcaption class="figure-caption">Situation with multiple endings where slurs don't end/start on a specific note.</figcaption>
</figure>

### Inserting Dynamics and Directives

Dynamics can be added with the hotkey "D" (placed above by default) or "Ctrl + D" (to place below). The default dynamic that is inserted is always "mf". It can be changed by editing the string between the tags.

**insert gif of editing dynamics in editor panel**

Dynamics can also be inserted over multiple notes and are treated like a spanning element, i.e. they get the attribute "endid". The dynamics will be extended by a dashed line. You can NOT insert dynamics for multiple staffs at once. If you select notes from multiple staffs mei-friend only adds them to the top staff.

For manipulating techniques see [manipulating]({{ site.baseurl }}/docs/basic/manipulating).
