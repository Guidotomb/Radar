# Dataviz Radar – QN

Dataviz interattive per la sezione Radar di Quotidiano Nazionale, pubblicate con GitHub Pages e incorporate nel CMS con un iframe.

Indice con anteprime e snippet: https://guidotomb.github.io/Radar/

## Dataviz

| Dataviz | URL | Dati | Fonte | Note |
|---|---|---|---|---|
| Meno bar, più ristoranti: come cambia l'Italia | https://guidotomb.github.io/Radar/bar-ristoranti/ | `data/bar-ristoranti.csv` | FIPE–Centro Studi Tagliacarne, *Pubblici esercizi e movida*, giugno 2026, p. 7 | Il dato 2025 si riferisce al primo semestre. |
| Non tutti i bar scomparsi hanno chiuso | https://guidotomb.github.io/Radar/bar-uscite/ | `data/bar-uscite.csv` | FIPE, *Rapporto Ristorazione 2026*, p. 46, su dati InfoCamere | Valori del testo FIPE (p. 46), non quelli invertiti nella figura. Le destinazioni sono solo quote sulle 4.679 riclassificazioni: la fonte non dà i conteggi. |
| La giornata del bar italiano | https://guidotomb.github.io/Radar/bar-giornata/ | `data/bar-giornata.csv, data/bar-giornata-totale.csv` | FIPE, *Rapporto Ristorazione 2026*, pp. 46-47, su dati TradeLab | Quote per occasione di consumo, 2025: nessuna distribuzione per ora. Le visite in miliardi per occasione sono un calcolo Radar. |
| Gli italiani escono meno: le pause pagano il prezzo più alto | https://guidotomb.github.io/Radar/visite-occasioni/ | `data/visite-occasioni.csv` | FIPE–TradeLab, *Rapporto Ristorazione 2026*, p. 110 | Visite nell'intero mercato dei consumi alimentari fuori casa, non solo nei bar. Nessuna attribuzione di cause. |
| Pochi giovani e pochissime donne alla guida degli autobus | https://guidotomb.github.io/Radar/autisti-eta-genere/ | `data/autisti-eta.csv, data/autisti-donne.csv` | Basco&T, in Agens 2025 | Età e genere vengono dalla stessa rilevazione ma non sono incrociati. Confronto europeo (IRU 2023) solo in nota. |
| Nei Paesi Bassi manca un autista su cinque | https://guidotomb.github.io/Radar/autisti-europa/ | `data/autisti-europa.csv, data/autisti-europa-confini.geojson` | IRU, Driver Shortage Report 2023; confini © EuroGeographics (GISCO) | Francia come intervallo (7-11%). Paesi senza stima nazionale in grigio. Confini GISCO 20M 2020, semplificati. |
| Le patenti per guidare l'autobus sono crollate | https://guidotomb.github.io/Radar/autisti-patenti-d/ | `data/autisti-patenti-d.csv` | MIT, Esiti esami 2011 e 2025; Agens 2025 (2004-2005) | Esami superati, non persone. −79% calcolato sul 2001, come nell'articolo. |
| Diventare autista può costare più di tre stipendi | https://guidotomb.github.io/Radar/autisti-costi-patente/ | `data/autisti-costi.csv` | MIT, Ccnl autoferrotranvieri, ACI, autoscuole e agenzie per il lavoro | Forchette di costo indicative. Stipendio netto d'ingresso: stima Radar sul minimo contrattuale (parametro 140, 14 mensilità). Selettore per fascia d'età (18-35 anni con bonus, oltre 35 senza). Fondi del bonus esauriti. |
| Stessi soldi per ogni donna, bisogni diversi | https://guidotomb.github.io/Radar/reddito-liberta-regioni/ | `data/rdl-regioni.csv, data/regioni-italia.geojson` | Dipartimento per le Pari opportunità, Inps (messaggio 3110/2026), Istat, Il Resto del Carlino | Budget 2026 = quote statali (10 + 1 + 5,5 milioni) + straordinaria (3,9 milioni). La quota di 5,5 milioni è ripartita con lo stesso criterio demografico (popolazione femminile 18-67 anni). Assegni pieni = budget / 6.360 €. Richieste di aiuto al 1522 nel 2024 ogni 100mila donne 18-67: calcolo Radar. Per l'Istat sono le persone che chiamano per chiedere aiuto per sé o per segnalare casi di violenza. Trentino-Alto Adige fuori dal riparto. Confini regionali semplificati. |
| Anche nello stesso ruolo, le donne guadagnano meno | https://guidotomb.github.io/Radar/retribuzioni-inquadramento/ | `data/retribuzioni-inquadramento.csv` | ODM Consulting (Gi Group Holding), Rapporto retribuzioni 2026 | Divario = (uomini − donne) / uomini. Data «è come se lavorasse gratis dal»: giorni non pagati = divario × 365, arrotondati, contati dal 31 dicembre. Mesi di reddito di libertà = differenza / 530 €. |
| Ogni 25 novembre il 1522 squilla di più | https://guidotomb.github.io/Radar/1522-settimane/ | `data/1522-settimanale.csv` | Istat su dati del Dipartimento per le Pari opportunità | Richieste di aiuto per settimana (domenica-sabato; per l'Istat, chi chiama per chiedere aiuto per sé o per segnalare casi di violenza), gennaio 2013 - settembre 2024; escluse le settimane spezzate a inizio e fine anno. Gennaio-inizio febbraio 2023 incompleto (chiamate senza provincia): tratteggiato ed escluso dalle medie. Dal 2025 cambia la registrazione: dati non confrontabili. |

## Aggiornare un grafico

Ogni pagina legge il proprio CSV da `data/` (separatore `;`, virgola decimale, UTF-8): per aggiornare i numeri basta modificare il CSV.

## Snippet per il CMS

Lo script va incollato inline (mai richiamato da un file esterno). Se in un articolo ci sono più dataviz, può restare in ognuna: si attiva una volta sola.

### Meno bar, più ristoranti: come cambia l'Italia

```html
<iframe src="https://guidotomb.github.io/Radar/bar-ristoranti/" width="100%" height="790" frameborder="0" scrolling="no" title="Meno bar, più ristoranti: come cambia l'Italia"></iframe>
<script>
(function(){if(window.__radarQNv2)return;window.__radarQNv2=1;var O="https://guidotomb.github.io";var MQ=window.matchMedia("(prefers-color-scheme:dark)");function frames(){return Array.prototype.filter.call(document.getElementsByTagName("iframe"),function(f){return(f.getAttribute("src")||"").indexOf(O+"/")===0;});}function theme(){var t=document.documentElement.getAttribute("data-theme");return t==="dark"||t==="light"?t:(MQ.matches?"dark":"light");}function bgOf(el){for(;el&&el.nodeType===1;el=el.parentElement){var c=getComputedStyle(el).backgroundColor;if(c&&c !=="transparent"&&!/rgba\([^)]*,\s*0\)$/.test(c))return c;}return null;}function send(f){try{f.contentWindow.postMessage({sentinel:"radar-qn",type:"theme",theme:theme(),bg:bgOf(f.parentElement)},O);}catch(e){}}function sendAll(){frames().forEach(send);}window.addEventListener("message",function(e){if(e.origin !==O)return;var d=e.data;if(!d||d.sentinel !=="radar-qn"||d.type !=="height")return;frames().forEach(function(f){if(f.contentWindow !==e.source)return;var h=Math.ceil(+d.height);if(h > 0&&20000 > h)f.style.height=h+"px";send(f);});});new MutationObserver(function(){sendAll();setTimeout(sendAll,400);}).observe(document.documentElement,{attributes:true,attributeFilter:["data-theme"]});if(MQ.addEventListener)MQ.addEventListener("change",sendAll);})();
</script>
```

### Non tutti i bar scomparsi hanno chiuso

```html
<iframe src="https://guidotomb.github.io/Radar/bar-uscite/" width="100%" height="950" frameborder="0" scrolling="no" title="Non tutti i bar scomparsi hanno chiuso"></iframe>
<script>
(function(){if(window.__radarQNv2)return;window.__radarQNv2=1;var O="https://guidotomb.github.io";var MQ=window.matchMedia("(prefers-color-scheme:dark)");function frames(){return Array.prototype.filter.call(document.getElementsByTagName("iframe"),function(f){return(f.getAttribute("src")||"").indexOf(O+"/")===0;});}function theme(){var t=document.documentElement.getAttribute("data-theme");return t==="dark"||t==="light"?t:(MQ.matches?"dark":"light");}function bgOf(el){for(;el&&el.nodeType===1;el=el.parentElement){var c=getComputedStyle(el).backgroundColor;if(c&&c !=="transparent"&&!/rgba\([^)]*,\s*0\)$/.test(c))return c;}return null;}function send(f){try{f.contentWindow.postMessage({sentinel:"radar-qn",type:"theme",theme:theme(),bg:bgOf(f.parentElement)},O);}catch(e){}}function sendAll(){frames().forEach(send);}window.addEventListener("message",function(e){if(e.origin !==O)return;var d=e.data;if(!d||d.sentinel !=="radar-qn"||d.type !=="height")return;frames().forEach(function(f){if(f.contentWindow !==e.source)return;var h=Math.ceil(+d.height);if(h > 0&&20000 > h)f.style.height=h+"px";send(f);});});new MutationObserver(function(){sendAll();setTimeout(sendAll,400);}).observe(document.documentElement,{attributes:true,attributeFilter:["data-theme"]});if(MQ.addEventListener)MQ.addEventListener("change",sendAll);})();
</script>
```

### La giornata del bar italiano

```html
<iframe src="https://guidotomb.github.io/Radar/bar-giornata/" width="100%" height="700" frameborder="0" scrolling="no" title="La giornata del bar italiano"></iframe>
<script>
(function(){if(window.__radarQNv2)return;window.__radarQNv2=1;var O="https://guidotomb.github.io";var MQ=window.matchMedia("(prefers-color-scheme:dark)");function frames(){return Array.prototype.filter.call(document.getElementsByTagName("iframe"),function(f){return(f.getAttribute("src")||"").indexOf(O+"/")===0;});}function theme(){var t=document.documentElement.getAttribute("data-theme");return t==="dark"||t==="light"?t:(MQ.matches?"dark":"light");}function bgOf(el){for(;el&&el.nodeType===1;el=el.parentElement){var c=getComputedStyle(el).backgroundColor;if(c&&c !=="transparent"&&!/rgba\([^)]*,\s*0\)$/.test(c))return c;}return null;}function send(f){try{f.contentWindow.postMessage({sentinel:"radar-qn",type:"theme",theme:theme(),bg:bgOf(f.parentElement)},O);}catch(e){}}function sendAll(){frames().forEach(send);}window.addEventListener("message",function(e){if(e.origin !==O)return;var d=e.data;if(!d||d.sentinel !=="radar-qn"||d.type !=="height")return;frames().forEach(function(f){if(f.contentWindow !==e.source)return;var h=Math.ceil(+d.height);if(h > 0&&20000 > h)f.style.height=h+"px";send(f);});});new MutationObserver(function(){sendAll();setTimeout(sendAll,400);}).observe(document.documentElement,{attributes:true,attributeFilter:["data-theme"]});if(MQ.addEventListener)MQ.addEventListener("change",sendAll);})();
</script>
```

### Gli italiani escono meno: le pause pagano il prezzo più alto

```html
<iframe src="https://guidotomb.github.io/Radar/visite-occasioni/" width="100%" height="910" frameborder="0" scrolling="no" title="Gli italiani escono meno: le pause pagano il prezzo più alto"></iframe>
<script>
(function(){if(window.__radarQNv2)return;window.__radarQNv2=1;var O="https://guidotomb.github.io";var MQ=window.matchMedia("(prefers-color-scheme:dark)");function frames(){return Array.prototype.filter.call(document.getElementsByTagName("iframe"),function(f){return(f.getAttribute("src")||"").indexOf(O+"/")===0;});}function theme(){var t=document.documentElement.getAttribute("data-theme");return t==="dark"||t==="light"?t:(MQ.matches?"dark":"light");}function bgOf(el){for(;el&&el.nodeType===1;el=el.parentElement){var c=getComputedStyle(el).backgroundColor;if(c&&c !=="transparent"&&!/rgba\([^)]*,\s*0\)$/.test(c))return c;}return null;}function send(f){try{f.contentWindow.postMessage({sentinel:"radar-qn",type:"theme",theme:theme(),bg:bgOf(f.parentElement)},O);}catch(e){}}function sendAll(){frames().forEach(send);}window.addEventListener("message",function(e){if(e.origin !==O)return;var d=e.data;if(!d||d.sentinel !=="radar-qn"||d.type !=="height")return;frames().forEach(function(f){if(f.contentWindow !==e.source)return;var h=Math.ceil(+d.height);if(h > 0&&20000 > h)f.style.height=h+"px";send(f);});});new MutationObserver(function(){sendAll();setTimeout(sendAll,400);}).observe(document.documentElement,{attributes:true,attributeFilter:["data-theme"]});if(MQ.addEventListener)MQ.addEventListener("change",sendAll);})();
</script>
```

### Pochi giovani e pochissime donne alla guida degli autobus

```html
<iframe src="https://guidotomb.github.io/Radar/autisti-eta-genere/" width="100%" height="820" frameborder="0" scrolling="no" title="Pochi giovani e pochissime donne alla guida degli autobus"></iframe>
<script>
(function(){if(window.__radarQNv2)return;window.__radarQNv2=1;var O="https://guidotomb.github.io";var MQ=window.matchMedia("(prefers-color-scheme:dark)");function frames(){return Array.prototype.filter.call(document.getElementsByTagName("iframe"),function(f){return(f.getAttribute("src")||"").indexOf(O+"/")===0;});}function theme(){var t=document.documentElement.getAttribute("data-theme");return t==="dark"||t==="light"?t:(MQ.matches?"dark":"light");}function bgOf(el){for(;el&&el.nodeType===1;el=el.parentElement){var c=getComputedStyle(el).backgroundColor;if(c&&c !=="transparent"&&!/rgba\([^)]*,\s*0\)$/.test(c))return c;}return null;}function send(f){try{f.contentWindow.postMessage({sentinel:"radar-qn",type:"theme",theme:theme(),bg:bgOf(f.parentElement)},O);}catch(e){}}function sendAll(){frames().forEach(send);}window.addEventListener("message",function(e){if(e.origin !==O)return;var d=e.data;if(!d||d.sentinel !=="radar-qn"||d.type !=="height")return;frames().forEach(function(f){if(f.contentWindow !==e.source)return;var h=Math.ceil(+d.height);if(h > 0&&20000 > h)f.style.height=h+"px";send(f);});});new MutationObserver(function(){sendAll();setTimeout(sendAll,400);}).observe(document.documentElement,{attributes:true,attributeFilter:["data-theme"]});if(MQ.addEventListener)MQ.addEventListener("change",sendAll);})();
</script>
```

### Nei Paesi Bassi manca un autista su cinque

```html
<iframe src="https://guidotomb.github.io/Radar/autisti-europa/" width="100%" height="760" frameborder="0" scrolling="no" title="Nei Paesi Bassi manca un autista su cinque"></iframe>
<script>
(function(){if(window.__radarQNv2)return;window.__radarQNv2=1;var O="https://guidotomb.github.io";var MQ=window.matchMedia("(prefers-color-scheme:dark)");function frames(){return Array.prototype.filter.call(document.getElementsByTagName("iframe"),function(f){return(f.getAttribute("src")||"").indexOf(O+"/")===0;});}function theme(){var t=document.documentElement.getAttribute("data-theme");return t==="dark"||t==="light"?t:(MQ.matches?"dark":"light");}function bgOf(el){for(;el&&el.nodeType===1;el=el.parentElement){var c=getComputedStyle(el).backgroundColor;if(c&&c !=="transparent"&&!/rgba\([^)]*,\s*0\)$/.test(c))return c;}return null;}function send(f){try{f.contentWindow.postMessage({sentinel:"radar-qn",type:"theme",theme:theme(),bg:bgOf(f.parentElement)},O);}catch(e){}}function sendAll(){frames().forEach(send);}window.addEventListener("message",function(e){if(e.origin !==O)return;var d=e.data;if(!d||d.sentinel !=="radar-qn"||d.type !=="height")return;frames().forEach(function(f){if(f.contentWindow !==e.source)return;var h=Math.ceil(+d.height);if(h > 0&&20000 > h)f.style.height=h+"px";send(f);});});new MutationObserver(function(){sendAll();setTimeout(sendAll,400);}).observe(document.documentElement,{attributes:true,attributeFilter:["data-theme"]});if(MQ.addEventListener)MQ.addEventListener("change",sendAll);})();
</script>
```

### Le patenti per guidare l'autobus sono crollate

```html
<iframe src="https://guidotomb.github.io/Radar/autisti-patenti-d/" width="100%" height="650" frameborder="0" scrolling="no" title="Le patenti per guidare l&#x27;autobus sono crollate"></iframe>
<script>
(function(){if(window.__radarQNv2)return;window.__radarQNv2=1;var O="https://guidotomb.github.io";var MQ=window.matchMedia("(prefers-color-scheme:dark)");function frames(){return Array.prototype.filter.call(document.getElementsByTagName("iframe"),function(f){return(f.getAttribute("src")||"").indexOf(O+"/")===0;});}function theme(){var t=document.documentElement.getAttribute("data-theme");return t==="dark"||t==="light"?t:(MQ.matches?"dark":"light");}function bgOf(el){for(;el&&el.nodeType===1;el=el.parentElement){var c=getComputedStyle(el).backgroundColor;if(c&&c !=="transparent"&&!/rgba\([^)]*,\s*0\)$/.test(c))return c;}return null;}function send(f){try{f.contentWindow.postMessage({sentinel:"radar-qn",type:"theme",theme:theme(),bg:bgOf(f.parentElement)},O);}catch(e){}}function sendAll(){frames().forEach(send);}window.addEventListener("message",function(e){if(e.origin !==O)return;var d=e.data;if(!d||d.sentinel !=="radar-qn"||d.type !=="height")return;frames().forEach(function(f){if(f.contentWindow !==e.source)return;var h=Math.ceil(+d.height);if(h > 0&&20000 > h)f.style.height=h+"px";send(f);});});new MutationObserver(function(){sendAll();setTimeout(sendAll,400);}).observe(document.documentElement,{attributes:true,attributeFilter:["data-theme"]});if(MQ.addEventListener)MQ.addEventListener("change",sendAll);})();
</script>
```

### Diventare autista può costare più di tre stipendi

```html
<iframe src="https://guidotomb.github.io/Radar/autisti-costi-patente/" width="100%" height="670" frameborder="0" scrolling="no" title="Diventare autista può costare più di tre stipendi"></iframe>
<script>
(function(){if(window.__radarQNv2)return;window.__radarQNv2=1;var O="https://guidotomb.github.io";var MQ=window.matchMedia("(prefers-color-scheme:dark)");function frames(){return Array.prototype.filter.call(document.getElementsByTagName("iframe"),function(f){return(f.getAttribute("src")||"").indexOf(O+"/")===0;});}function theme(){var t=document.documentElement.getAttribute("data-theme");return t==="dark"||t==="light"?t:(MQ.matches?"dark":"light");}function bgOf(el){for(;el&&el.nodeType===1;el=el.parentElement){var c=getComputedStyle(el).backgroundColor;if(c&&c !=="transparent"&&!/rgba\([^)]*,\s*0\)$/.test(c))return c;}return null;}function send(f){try{f.contentWindow.postMessage({sentinel:"radar-qn",type:"theme",theme:theme(),bg:bgOf(f.parentElement)},O);}catch(e){}}function sendAll(){frames().forEach(send);}window.addEventListener("message",function(e){if(e.origin !==O)return;var d=e.data;if(!d||d.sentinel !=="radar-qn"||d.type !=="height")return;frames().forEach(function(f){if(f.contentWindow !==e.source)return;var h=Math.ceil(+d.height);if(h > 0&&20000 > h)f.style.height=h+"px";send(f);});});new MutationObserver(function(){sendAll();setTimeout(sendAll,400);}).observe(document.documentElement,{attributes:true,attributeFilter:["data-theme"]});if(MQ.addEventListener)MQ.addEventListener("change",sendAll);})();
</script>
```

### Stessi soldi per ogni donna, bisogni diversi

```html
<iframe src="https://guidotomb.github.io/Radar/reddito-liberta-regioni/" width="100%" height="1080" frameborder="0" scrolling="no" title="Stessi soldi per ogni donna, bisogni diversi"></iframe>
<script>
(function(){if(window.__radarQNv2)return;window.__radarQNv2=1;var O="https://guidotomb.github.io";var MQ=window.matchMedia("(prefers-color-scheme:dark)");function frames(){return Array.prototype.filter.call(document.getElementsByTagName("iframe"),function(f){return(f.getAttribute("src")||"").indexOf(O+"/")===0;});}function theme(){var t=document.documentElement.getAttribute("data-theme");return t==="dark"||t==="light"?t:(MQ.matches?"dark":"light");}function bgOf(el){for(;el&&el.nodeType===1;el=el.parentElement){var c=getComputedStyle(el).backgroundColor;if(c&&c !=="transparent"&&!/rgba\([^)]*,\s*0\)$/.test(c))return c;}return null;}function send(f){try{f.contentWindow.postMessage({sentinel:"radar-qn",type:"theme",theme:theme(),bg:bgOf(f.parentElement)},O);}catch(e){}}function sendAll(){frames().forEach(send);}window.addEventListener("message",function(e){if(e.origin !==O)return;var d=e.data;if(!d||d.sentinel !=="radar-qn"||d.type !=="height")return;frames().forEach(function(f){if(f.contentWindow !==e.source)return;var h=Math.ceil(+d.height);if(h > 0&&20000 > h)f.style.height=h+"px";send(f);});});new MutationObserver(function(){sendAll();setTimeout(sendAll,400);}).observe(document.documentElement,{attributes:true,attributeFilter:["data-theme"]});if(MQ.addEventListener)MQ.addEventListener("change",sendAll);})();
</script>
```

### Anche nello stesso ruolo, le donne guadagnano meno

```html
<iframe src="https://guidotomb.github.io/Radar/retribuzioni-inquadramento/" width="100%" height="720" frameborder="0" scrolling="no" title="Anche nello stesso ruolo, le donne guadagnano meno"></iframe>
<script>
(function(){if(window.__radarQNv2)return;window.__radarQNv2=1;var O="https://guidotomb.github.io";var MQ=window.matchMedia("(prefers-color-scheme:dark)");function frames(){return Array.prototype.filter.call(document.getElementsByTagName("iframe"),function(f){return(f.getAttribute("src")||"").indexOf(O+"/")===0;});}function theme(){var t=document.documentElement.getAttribute("data-theme");return t==="dark"||t==="light"?t:(MQ.matches?"dark":"light");}function bgOf(el){for(;el&&el.nodeType===1;el=el.parentElement){var c=getComputedStyle(el).backgroundColor;if(c&&c !=="transparent"&&!/rgba\([^)]*,\s*0\)$/.test(c))return c;}return null;}function send(f){try{f.contentWindow.postMessage({sentinel:"radar-qn",type:"theme",theme:theme(),bg:bgOf(f.parentElement)},O);}catch(e){}}function sendAll(){frames().forEach(send);}window.addEventListener("message",function(e){if(e.origin !==O)return;var d=e.data;if(!d||d.sentinel !=="radar-qn"||d.type !=="height")return;frames().forEach(function(f){if(f.contentWindow !==e.source)return;var h=Math.ceil(+d.height);if(h > 0&&20000 > h)f.style.height=h+"px";send(f);});});new MutationObserver(function(){sendAll();setTimeout(sendAll,400);}).observe(document.documentElement,{attributes:true,attributeFilter:["data-theme"]});if(MQ.addEventListener)MQ.addEventListener("change",sendAll);})();
</script>
```

### Ogni 25 novembre il 1522 squilla di più

```html
<iframe src="https://guidotomb.github.io/Radar/1522-settimane/" width="100%" height="750" frameborder="0" scrolling="no" title="Ogni 25 novembre il 1522 squilla di più"></iframe>
<script>
(function(){if(window.__radarQNv2)return;window.__radarQNv2=1;var O="https://guidotomb.github.io";var MQ=window.matchMedia("(prefers-color-scheme:dark)");function frames(){return Array.prototype.filter.call(document.getElementsByTagName("iframe"),function(f){return(f.getAttribute("src")||"").indexOf(O+"/")===0;});}function theme(){var t=document.documentElement.getAttribute("data-theme");return t==="dark"||t==="light"?t:(MQ.matches?"dark":"light");}function bgOf(el){for(;el&&el.nodeType===1;el=el.parentElement){var c=getComputedStyle(el).backgroundColor;if(c&&c !=="transparent"&&!/rgba\([^)]*,\s*0\)$/.test(c))return c;}return null;}function send(f){try{f.contentWindow.postMessage({sentinel:"radar-qn",type:"theme",theme:theme(),bg:bgOf(f.parentElement)},O);}catch(e){}}function sendAll(){frames().forEach(send);}window.addEventListener("message",function(e){if(e.origin !==O)return;var d=e.data;if(!d||d.sentinel !=="radar-qn"||d.type !=="height")return;frames().forEach(function(f){if(f.contentWindow !==e.source)return;var h=Math.ceil(+d.height);if(h > 0&&20000 > h)f.style.height=h+"px";send(f);});});new MutationObserver(function(){sendAll();setTimeout(sendAll,400);}).observe(document.documentElement,{attributes:true,attributeFilter:["data-theme"]});if(MQ.addEventListener)MQ.addEventListener("change",sendAll);})();
</script>
```
