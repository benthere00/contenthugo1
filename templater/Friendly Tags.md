Keywords: <%* 
const theseTags = tp.file.tags;
let tagStr = theseTags.join(',');
tagStr = tagStr.replace(/\#/g,''); 
tR += tagStr;
%>