---
layout: default
---

Bem-vindos
<div id="anchor" />
<input type="button" value="Activate" onclick="activate()" />

<script language="javascript">

function activate() {
    var text = document.createTextNode('Activated');
    var anchor = document.getElementById('anchor');
    anchor.parentNode.insertBefore(text, anchor);
}

</script>