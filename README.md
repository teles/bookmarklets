# Bookmarklets

A list of useful bookmarklets for daily usage

## General

### Prepend relative URLs with base URL

```JavaScript
const prependURL = window.prompt("Base URL to prepend", location.hostname)
Array.from(document.querySelectorAll("a[href]")).filter(a => {
    return a.getAttribute("href") !== a.href;    
}).forEach((a, index, anchors ) => {
    a.setAttribute("href", [
        prependURL.replace(/\/$/, ''), 
        a.getAttribute("href").replace(/^\//, '')
    ].join("/"));
    if(index === anchors.length -1) {
        window.alert(`Success: ${anchors.length} changed anchors`)
    }
})
```

### Show images without alt attribute

```JavaScript
const borderColor = window.prompt("Set a highlight color for images without alt", "red");
const imgs = Array.from(document.querySelectorAll("img:not([src])"));
imgs.forEach(img => img.style.border = `3px dashed ${borderColor}`);
window.alert(`This page has ${imgs.length || 0} images without alt attribute`);
```

### Fill in all inputs with their placeholder values

```JavaScript
document.querySelectorAll('input[placeholder]').forEach(input => input.value = input.placeholder);
```

### Fill in all inputs with placeholders plus timestamp

```JavaScript
const inputReplacers = {
    "email": (value) => value.replace(/(.*?)@(.*?)/, `$1+${new Date().getTime()}@$2`),
    "text": (value) => `${value} +${new Date().getTime()}`    
}
document.querySelectorAll('input[placeholder]').forEach(input => { 
    input.value = inputReplacers[input.type] ? inputReplacers[input.type](input.placeholder) : input.placeholder;    
});
```
