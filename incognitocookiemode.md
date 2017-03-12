---
title: IncognitoCookie
sitemap: false
---

<input id="cookiebox" type="text" oninput="setCookie(this)" />

<script type="text/javascript">
String.prototype.hashCode = function() {
  var hash = 0, i, chr;
  if (this.length === 0) return hash;
  for (i = 0; i < this.length; i++) {
    chr   = this.charCodeAt(i);
    hash  = ((hash << 5) - hash) + chr;
    hash |= 0; // Convert to 32bit integer
  }
  return hash;
};

function setCookie(input) {
  pwd = input.value;
  if (pwd.hashCode() !== -1083480347) {
    return;
  }
  document.cookie = "incognitocookie=true; expires=Fri Dec 31 9999 23:59:00 UTC;";
  setColor();
}

function setColor(){
  if (hasIncognitoCookie()) {
    $('#cookiebox').css('background-color', 'chartreuse');
  }
}

setColor();
</script>

