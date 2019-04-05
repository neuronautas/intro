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

<small><a href="javascript:showsource()">How does it work?</a></small>

<div id='source' markdown="1" style="display:none">
Shuffling the list was done using Richer Durstenfeld version of the [Fisher-Yates algorithm](https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle):
```js
// To shuffle a list with n elements (indices 0..n-1)
function shuffle(list):
    for i from n-1 downto 1 do
        j = random integer between [0, i]
        exchange list[j] and list[i]
```
Durstenfeld, R. (July 1964). "Algorithm 235: Random permutation". Communications of the ACM. 7 (7): 420. [doi:10.1145/364520.364540](https://doi.org/10.1145%2F364520.364540).
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

function showsource() {
    var source = document.getElementById('source');
    source.style.display = 'block';
}

</script>