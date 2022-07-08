---
id: z717mp17s35fzagmwi0tix2
title: Replace Text on Page
desc: ''
updated: 1657307620361
created: 1657307493774
---

if(document.location.pathname.indexOf('watches') > 0) {
  var ele = document.querySelector('.style .filter-title .filter-title-label');
  if(ele) ele.innerHTML = 'Year';
}


This looks for a page URL that contains the selected text.  If we match, then do anything you want (eg. replace a filter label)