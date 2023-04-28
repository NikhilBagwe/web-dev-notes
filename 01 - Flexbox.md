## Flexbox :

- Apply CSS property "display: flex" on the container.

# Properties that belong inside Container :

## flex-direction:

- By default "flex-direction" is set to horizontal or "row".
- It changes the direction of "Main axis".
- Can be set to : row, column.

## justify-content :

- Aligns items on the "main axis".
- Can be set to : flex-start, flex-end, center, 
- space-between (elements are totally spread out), 
- space-around (even the corner elements will have some space around them), 
- space-evenly (distributes space evenly between all items)

## align-items :

- Aligns items along the "cross axis" which is set to vertical by default.
- Can be set to : flex-start, flex-end, center, baseline
- In baseline, the flexbox items are aligned at the baseline of the cross axis.
- By default, the cross axis is vertical. This means the flexbox items will align themselves in order to have the baseline of their text align along a horizontal line.
- Reference : https://cssreference.io/property/align-items/#:~:text=align%2Ditems%3A%20baseline%3B,align%20along%20a%20horizontal%20line.

## flex-wrap :

- All items will try to fit into one line and start crushing each other unless we add flex-wrap property.
- By default set to "nowrap".
- Set it to "wrap".

## align-content :

- Only applies if "flex-wrap: wrap" is present, and if there are multiple lines of flexbox items, a new property is unlocked, the "align-content".
- Allows us to align items on Cross-axis.
- Can be set to : flex-start, flex-end, center, space-between, space-around, space-evenly

## gap :

- Increase distance/gap between flexbox-items.

# Properties that apply directly to childrens/items :

## flex-grow :

- Takes a unitless value that serves as a proportion and it allows an item to grow if there is enough space for it to grow.
- We have to apply this prop on the particular item.

## flex-shrink :

- Takes a unitless value and it specifies how fast an item shrinks in comparison to other.
- If value is set to >= 1, item will shrink.
- If set to "0", item will refuse to shrink.

## flex-basis :

- It defines the size of an item before the remaining space is disributed.
- Defines the initial size of a flexbox item.

## flex :

- Shorthand property for flex-grow, flex-shrink, flex-basis
- We have to set only one value, rest 2 are optional. They are automatically set if not mentioned.
- "flex: 1"

## align-self :

- Overwrites the value you set in "align-items" on the container.
- Suppose if I have set "align-items: flex-start" on container, but I want the first item to be aligned to center. We set "align-self: center".

## order:

- Change the order in which items appear.
- By default all items order is set to 0.
- If we want 3rd item to appear first, we set it's "order: -1".








