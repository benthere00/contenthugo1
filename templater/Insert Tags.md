<%*
const theseTags = tp.file.tags;
let tagArr = theseTags.map(tag => tag.replace(/^#/, ''));
tR += JSON.stringify(tagArr); 
%>