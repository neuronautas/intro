---
layout: default
---

Bem-vindos

<table>
  <thead>
    <tr><th>Neurocadetes</th><th></th></tr>
  </thead>
  <tbody id="table">
  </tbody>
</table>

<div>
  <div><textarea id="entries" cols="40" rows="5"></textarea></div>
  <div><input type="button" value="Activate" onclick="activate()" /></div>
</div>

<script language="javascript">

var draw = 0;
var maxDraws = 2;
var maxEntries = 16;

function shuffle(list) {
    for (var i = list.length - 1; i > 0; i--) {
        var index = Math.floor(Math.random() * (i + 1));
        var temp = list[i];
        list[i] = list[index];
        list[index] = temp;
    }
}

function activate() {
    var table = document.getElementById('table');
    var entries = document.getElementById('entries');
    var list = entries.value.split('\n').filter(Boolean);
    entries.value = '';
    shuffle(list);
    for (var i = 0; i < Math.min(list.length, maxEntries / maxDraws); i++) {
        var row = i < table.rows.length
            ? table.rows[i]
            : table.insertRow(table.rows.length);
        var cell = row.insertCell(draw);
        cell.innerHTML = list[i];
    }

    if (++draw == maxDraws) {
        entries.parentNode.parentNode.style.display = 'none';
    }
}

</script>