#把除了on, of等虚词之外的词改成词首大写，其余的小写，虚词则仅在句首的时候首字母大写
zoteroPane = Zotero.getActiveZoteroPane();
items = zoteroPane.getSelectedItems();
var result = "";
var ignoredWords = ["on", "of", "in", "at", "to", "with", "by", "for", "and"];
for (item of items) {
    var publicationTitle = item.getField('publicationTitle');
    result += " " + publicationTitle + "\n";
    var words = publicationTitle.split(' ');
    var new_title = '';
    for (var i = 0; i < words.length; i++) {
        var word = words[i];
        if (ignoredWords.includes(word.toLowerCase()) && i !== 0) {
            new_title += word.toLowerCase() + ' ';
        } else {
            new_title += word.charAt(0).toUpperCase() + word.slice(1).toLowerCase() + ' ';
        }
    }
    new_title = new_title.trim();
    result += "-> " + new_title + "\n\n";
    // Do it at your own risk
    item.setField('publicationTitle', new_title);
    await item.saveTx();
}
return result;
