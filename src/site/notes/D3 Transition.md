---
{"title":"D3 Transition","alias":null,"type":"note","created":"2022-12-01T22:17:14","modified":"2022-12-12T12:47:58","dg-publish":true,"sup":[["D3","d3"]],"state":"done","permalink":"/d3-transition/","dgPassFrontmatter":true,"updated":"2022-12-12T12:47:58"}
---


# D3 Transition

- `.transition().duration(time)` adds a transition to the change
    - `time` should be a [[JS Types - Number\|number]]; its unit is ms
    - these two methods should be between the selection and the change
        - <span class="alt-check alt-check-ex">`d3.select("svg").select("circle").transition().duration(2000).attr("cx", "400")`</span>
    - not all changes can be added with a transition
        - [+] changes in size and position can
        - [-] changes in font family cannot
    - we can add multiple transitions by chaining them
        - then the transitions will happen one by one
        - <span class="alt-check alt-check-ex">`d3.select("svg").select("circle").transition().duration(2000).attr("cx", "400").transition().duration(2000).attr("cy","200")`</span>

## Do and Not

Transitions in different statements run **simultaneously**. Therefore

- **DO**
    - Run simultaneous transitions on **different** selections
    - Run sequential transitions on the same selection in **one chain**
    - Transition from *something* to *something*
        - The attributes being transitioned should have an initial value before the transition
- **DO NOT**
    - Do not run two transitions on the same selection at the same time
        - i.e., in two statements/chains
    - Do not transition from *nothing* to something
    - Do not store a selection with a transition
        - it is not a selection object anymore
        - it becomes a `Transition` object
    - Do not put a transition before a [[D3 Bind Data#Merge\|merge]]
