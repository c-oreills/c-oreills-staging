---
title: IncognitoCookie
---

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
  document.cookie = "incognitocookie=true"
  $(input).css('background-color', 'chartreuse')
}

</script>

<input id="cookiebox" type="text" oninput="setCookie(this)" />
