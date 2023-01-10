# Bookmarklets

A list of useful bookmarklets for daily usage

## General

**Show images without alt attribute**

```JavaScript
const borderColor = window.prompt("Set a highlight color for images without alt", "red");
const imgs = Array.from(document.querySelectorAll("img:not([src])"));
imgs.forEach(img => img.style.border = `3px dashed ${borderColor}`);
window.alert(`This page has ${imgs.length || 0} images without alt attribute`);
```

