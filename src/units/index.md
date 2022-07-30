Estradiol (E2)

<div id="e2">
<label>
<input name="source" type="text"/>
pmol/l
</label>
<button><></button>
<label>
<input name="target" type="text"/>
pg/ml
</label>
<button>Reset</button>
</div>

Testosteron (TST)

<div id="tst">
<label>
<input name="source" type="text"/>
nmol/l
</label>
<button><></button>
<label>
<input name="target" type="text"/>
ng/ml
</label>
<button>Reset</button>
</div>

[Więcej](http://unitslab.com/)

<script>
function attachConversion(divElement, ratio) {
  let sourceInput;
  let targetInput;
  let convertButton;
  let resetButton;
  for(const el of divElement.getElementsByTagName("input")) {
    if(el.name === 'source') {
      sourceInput = el;
    }
    if(el.name === 'target') {
      targetInput = el;
    }
  }
  for(const el of divElement.getElementsByTagName("button")) {
    if(el.innerText === '<>') {
      convertButton = el;
    }
    if(el.innerText === 'Reset') {
      resetButton = el;
    }
  }

  resetButton.addEventListener("click", () => {
    sourceInput.value = "";
    targetInput.value = "";
  });

  convertButton.addEventListener("click", () => {
    let s = sourceInput.value.replace(",", ".").trim();
    let t = targetInput.value.replace(",", ".").trim();
    if(s && !t) {
       targetInput.value = (parseFloat(s)/ratio).toFixed(2);
    }
    if(!s && t) {
       sourceInput.value = (ratio/parseFloat(t)).toFixed(2);
    }
  });
}

attachConversion(document.getElementById("e2"), 100000/27238);
attachConversion(document.getElementById("tst"), 100000/28842);
</script>