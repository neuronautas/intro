---
layout: default
---

Bem-vindos

<table>
  <thead>
    <tr><th>Cadetes</th></tr>
  </thead>
  <tbody id="table">
  </tbody>
</table>

<div>
  <div><textarea id="entries" cols="40" rows="5"></textarea></div>
  <div><input type="button" value="Activate" onclick="activate()" /></div>
</div>

<script language="javascript">

function shuffle(list) {
    for (var i = list.length - 1; i > 0; i--) {
        var index = Math.floor(Math.random() * (i + 1));
        var temp = list[i];
        list[i] = list[index];
        list[index] = temp;
    }
}

function activate() {
    var maxEntries = 16;
    var table = document.getElementById('table');
    var entries = document.getElementById('entries');
    var list = entries.value.split('\n').filter(Boolean);
    entries.parentNode.parentNode.style.display = 'none';
    shuffle(list);
    for (var i = 0; i < Math.min(list.length, maxEntries); i++) {
        var row = table.insertRow(table.rows.length);
        var cell = row.insertCell(0);
        cell.innerHTML = list[i];
    }
}

</script>