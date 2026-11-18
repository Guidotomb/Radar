# Dataviz Radar – QN

Dataviz interattive per la sezione Radar di Quotidiano Nazionale, pubblicate con GitHub Pages e incorporate nel CMS con un iframe.

Indice con anteprime e snippet: https://guidotomb.github.io/Radar/

## Dataviz

| Dataviz | URL | Dati | Fonte | Note |
|---|---|---|---|---|
| Meno bar, più ristoranti: come cambia l'Italia | https://guidotomb.github.io/Radar/bar-ristoranti/ | `data/bar-ristoranti.csv` | FIPE–Centro Studi Tagliacarne, *Pubblici esercizi e movida*, giugno 2026, p. 7 | Il dato 2025 si riferisce al primo semestre. |
| Non tutti i bar scomparsi hanno chiuso | https://guidotomb.github.io/Radar/bar-uscite/ | `data/bar-uscite.csv` | FIPE, *Rapporto Ristorazione 2026*, p. 46, su dati InfoCamere | Valori del testo FIPE (p. 46), non quelli invertiti nella figura. Le destinazioni sono solo quote sulle 4.679 riclassificazioni: la fonte non dà i conteggi. |
| La giornata del bar italiano | https://guidotomb.github.io/Radar/bar-giornata/ | `data/bar-giornata.csv, data/bar-giornata-totale.csv` | FIPE, *Rapporto Ristorazione 2026*, pp. 46-47, su dati TradeLab | Quote per occasione di consumo, 2025: nessuna distribuzione per ora. Le visite in miliardi per occasione sono un calcolo Radar. |

## Aggiornare un grafico

Ogni pagina legge il proprio CSV da `data/` (separatore `;`, virgola decimale, UTF-8): per aggiornare i numeri basta modificare il CSV.

## Snippet per il CMS

Lo script va incollato inline (mai richiamato da un file esterno). Se in un articolo ci sono più dataviz, può restare in ognuna: si attiva una volta sola.

### Meno bar, più ristoranti: come cambia l'Italia

```html
<iframe src="https://guidotomb.github.io/Radar/bar-ristoranti/" width="100%" height="840" frameborder="0" scrolling="no" title="Meno bar, più ristoranti: come cambia l'Italia"></iframe>
<script>
(function(){if(window.__radarQNv2)return;window.__radarQNv2=1;var O="https://guidotomb.github.io";var MQ=window.matchMedia("(prefers-color-scheme:dark)");function frames(){return Array.prototype.filter.call(document.getElementsByTagName("iframe"),function(f){return(f.getAttribute("src")||"").indexOf(O+"/")===0;});}function theme(){var t=document.documentElement.getAttribute("data-theme");return t==="dark"||t==="light"?t:(MQ.matches?"dark":"light");}function bgOf(el){for(;el&&el.nodeType===1;el=el.parentElement){var c=getComputedStyle(el).backgroundColor;if(c&&c !=="transparent"&&!/rgba\([^)]*,\s*0\)$/.test(c))return c;}return null;}function send(f){try{f.contentWindow.postMessage({sentinel:"radar-qn",type:"theme",theme:theme(),bg:bgOf(f.parentElement)},O);}catch(e){}}function sendAll(){frames().forEach(send);}window.addEventListener("message",function(e){if(e.origin !==O)return;var d=e.data;if(!d||d.sentinel !=="radar-qn"||d.type !=="height")return;frames().forEach(function(f){if(f.contentWindow !==e.source)return;var h=Math.ceil(+d.height);if(h > 0&&20000 > h)f.style.height=h+"px";send(f);});});new MutationObserver(function(){sendAll();setTimeout(sendAll,400);}).observe(document.documentElement,{attributes:true,attributeFilter:["data-theme"]});if(MQ.addEventListener)MQ.addEventListener("change",sendAll);})();
</script>
```

### Non tutti i bar scomparsi hanno chiuso

```html
<iframe src="https://guidotomb.github.io/Radar/bar-uscite/" width="100%" height="930" frameborder="0" scrolling="no" title="Non tutti i bar scomparsi hanno chiuso"></iframe>
<script>
(function(){if(window.__radarQNv2)return;window.__radarQNv2=1;var O="https://guidotomb.github.io";var MQ=window.matchMedia("(prefers-color-scheme:dark)");function frames(){return Array.prototype.filter.call(document.getElementsByTagName("iframe"),function(f){return(f.getAttribute("src")||"").indexOf(O+"/")===0;});}function theme(){var t=document.documentElement.getAttribute("data-theme");return t==="dark"||t==="light"?t:(MQ.matches?"dark":"light");}function bgOf(el){for(;el&&el.nodeType===1;el=el.parentElement){var c=getComputedStyle(el).backgroundColor;if(c&&c !=="transparent"&&!/rgba\([^)]*,\s*0\)$/.test(c))return c;}return null;}function send(f){try{f.contentWindow.postMessage({sentinel:"radar-qn",type:"theme",theme:theme(),bg:bgOf(f.parentElement)},O);}catch(e){}}function sendAll(){frames().forEach(send);}window.addEventListener("message",function(e){if(e.origin !==O)return;var d=e.data;if(!d||d.sentinel !=="radar-qn"||d.type !=="height")return;frames().forEach(function(f){if(f.contentWindow !==e.source)return;var h=Math.ceil(+d.height);if(h > 0&&20000 > h)f.style.height=h+"px";send(f);});});new MutationObserver(function(){sendAll();setTimeout(sendAll,400);}).observe(document.documentElement,{attributes:true,attributeFilter:["data-theme"]});if(MQ.addEventListener)MQ.addEventListener("change",sendAll);})();
</script>
```

### La giornata del bar italiano

```html
<iframe src="https://guidotomb.github.io/Radar/bar-giornata/" width="100%" height="850" frameborder="0" scrolling="no" title="La giornata del bar italiano"></iframe>
<script>
(function(){if(window.__radarQNv2)return;window.__radarQNv2=1;var O="https://guidotomb.github.io";var MQ=window.matchMedia("(prefers-color-scheme:dark)");function frames(){return Array.prototype.filter.call(document.getElementsByTagName("iframe"),function(f){return(f.getAttribute("src")||"").indexOf(O+"/")===0;});}function theme(){var t=document.documentElement.getAttribute("data-theme");return t==="dark"||t==="light"?t:(MQ.matches?"dark":"light");}function bgOf(el){for(;el&&el.nodeType===1;el=el.parentElement){var c=getComputedStyle(el).backgroundColor;if(c&&c !=="transparent"&&!/rgba\([^)]*,\s*0\)$/.test(c))return c;}return null;}function send(f){try{f.contentWindow.postMessage({sentinel:"radar-qn",type:"theme",theme:theme(),bg:bgOf(f.parentElement)},O);}catch(e){}}function sendAll(){frames().forEach(send);}window.addEventListener("message",function(e){if(e.origin !==O)return;var d=e.data;if(!d||d.sentinel !=="radar-qn"||d.type !=="height")return;frames().forEach(function(f){if(f.contentWindow !==e.source)return;var h=Math.ceil(+d.height);if(h > 0&&20000 > h)f.style.height=h+"px";send(f);});});new MutationObserver(function(){sendAll();setTimeout(sendAll,400);}).observe(document.documentElement,{attributes:true,attributeFilter:["data-theme"]});if(MQ.addEventListener)MQ.addEventListener("change",sendAll);})();
</script>
```
