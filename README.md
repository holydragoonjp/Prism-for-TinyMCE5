# Prism-for-TinyMCE5

## 【日本語】
### このプラグインは何？
TinyMCE5にPrism.js（ https://prismjs.com/ ）用のボタンを追加して、シンタックスハイライトを表示させるためのプラグインです。

### 使用方法
prismフォルダを中身ごとご利用になられているサーバーのTinyMCE5の本体を入れているフォルダのpluginフォルダの中に、FTPなどを利用して
アスキーモードでアップロードしてください。

次にこのプラグインを利用するために、TinyMCE5の設定であるtinymce.initのpluginsの中と、toolbarの中にそれぞれprism を挿入してください。
例）
<pre><code>plugins: [
	'advlist autolink lists link image charmap print preview anchor pagebreak prism'
],
toolbar: ' undo redo | bold italic strikethrough | bullist numlist | link pagebreak code prism ',</code></pre>
（上の例では、それぞれの設定の一番最後にprismが挿入されています）
挿入できたらtinymce.initを記載しているファイルをプラグインの本体と同じく、FTPなどでサーバーにアップロードしてください。
これで作成されたPrismプラグインのボタンをクリックしたり、メニューアイテムからPrismを選択したりすると、Markup、css、C-like、JavaScriptの４つの言語がポップアップウィンドウのプルダウンメニュー内に表示されます。
その下のテキストエリア内にシンタックスハイライトで表示したいコードを記入してください。
また、特定の文字列をドラッグして選択した状態で、Prismプラグインのボタンをクリックする、メニューアイテムのPrismプラグインを選択すると、テキストエリア内にドラッグして選択した特定の文字列が自動挿入されます。

Prismでシンタックスハイライトとして表示される&lt;pre&gt;&lt;code class="language-xx"&gt;～～&lt;/code&gt;&lt;/pre&gt;のタグに囲われた文字列にカーソルを合わせると、Prismプラグインのボタンが反転します。その状態でボタンをクリックすると、&lt;pre&gt;&lt;code class="language-xx"&gt;～～&lt;/code&gt;&lt;/pre&gt;のタグを消去することができます。
指定したスクリプト言語を間違えたときなど、タグを修正したい場合にご利用ください。
また、&lt;pre&gt;&lt;/pre&gt;で囲われていない&lt;code&gt;～～&lt;/code&gt;タグもボタンのクリックで消去できるようになっております。
（こちらはボタンの反転はありませんが、&lt;code&gt;&lt;/code&gt;タグが残っている状態でその中に&lt;pre&gt;&lt;code class="language-xx"&gt;～～&lt;/code&gt;&lt;/pre&gt;のタグが生成されると、記述的におかしなことになってしまうと思うので、こういった機能にしています）

### プラグインのプルダウンメニューで表示させたいスクリプト言語を指定する方法
Prismでは多数のスクリプト言語に対応しています。Prismのインストール時にそれらの言語を自由に選択して導入できるため、人それぞれの利用状況によってプルダウンメニュー内に表示させたい言語は違ってくると思います。
そこで当プラグインでは、tinymce.initの中にprism_languagesという項目を記入し、その中に{text: '○○', value: '○○'},という形式でPrismで利用している言語の一覧を入れることで、Prismプラグイン内で表示させることができます。prism_languagesの項目が記入されていなければ、使用方法の中で記載した４言語が表示されます。

例えば、Markup、JavaScript、css、PHP、SQL、Smarty、Iniの７言語をプルダウンメニューに表示させたい場合は、以下のような記述となります。
<pre><code>prism_languages: [
	{text: 'HTML/XML',   value: 'markup'},
	{text: 'JavaScript', value: 'javascript'},
	{text: 'CSS',        value: 'css'},
	{text: 'PHP',        value: 'php'},
	{text: 'SQL',        value: 'sql'},
	{text: 'Smarty',     value: 'smarty'},
	{text: 'Ini',        value: 'ini'}
],</code></pre>
text:''にそれぞれの言語名、value:''にPrismの公式サイト（ https://prismjs.com/ ）のSupported languagesで解説されているlanguage-○○の『○○』の部分を入れ、\{\}で囲ってください。
複数記入する際には\}（波括弧閉じる）の後ろに必ず,（コンマ）を入れてください。ただし、例外として最終行はなくても大丈夫です。入れ忘れるとエラーの原因となりますのでご注意ください。


### 行番号を表示非表示にしたり、先頭行の行番号を指定したり、強調したい行を指定する方法
Prismではプラグインの導入により、様々な表示をさせることができます。
当プラグインは、PrismにLine NumbersとLine Highlightを導入していることを想定して作成しております。
ポップアップウィンドウの下部にある、『行番号を表示』にチェックを入れたり切ったりすることで行番号の表示/非表示を選べます（デフォルトでは行番号が入るように設定してあります）。
『開始行の番号』は一番最初の行に入れたい行番号を指定することができます。以上２種がLine Numbersの機能を利用しています。
『強調したい行』はLine Highlightの機能を利用して、強調表示をしたい行を指定できます。指定方法もPrismの公式サイトで解説されている方法が利用できます。
また、『行番号を表示』にチェックが入っていない場合、『開始行の番号』や『強調したい行』にデータを入れてもそれらのデータが挿入したコードに反映されない仕様となっています。そのため、『行番号を表示』のチェックを切ると同時に、『開始行の番号』、『強調したい行』の一行入力のエリアが入力不可（disable）となるように設計しております。


### ご注意
このプラグインは一個人が試行錯誤し作成したものです。
そのため不具合が生じることがございます。

当プラグインを使用などしたことによって生じた損害は、一切の責任を負いません。


### プラグインの削除方法
1. TinyMCEのフォルダに含まれている、pluginフォルダ内のprismフォルダをサーバーから削除。
2. tinymce.initのpluginsやtoolbar内に記載したprismの文字列を削除し、prism_languagesを指定している場合は、prism_languages: \[～～\]の記載を削除して、tinymce.initが含まれているファイルをサーバーにアップロードしてください。

- - - - -

## 【English】
### What is this plugin?
This is a plugin for adding syntax highlighting by adding a button of Prism.js (https://prismjs.com/) to TinyMCE 4.

### Usage
In the plugin folder of the folder of the TinyMCE 4 of the server that is used by the contents, use ASCII Please upload in mode.

In order to use this plugin, please insert "prism" into plugins and toolbar of tinymce.init which is the setting of TinyMCE 4 respectively.
For Example:
<pre><code>plugins: [
	'advlist autolink lists link image charmap print preview anchor pagebreak prism'
],
toolbar: ' undo redo | bold italic strikethrough | bullist numlist | link pagebreak code prism ',</code></pre>
In the above example, prism is inserted at the end of each setting.
Please upload the file describing tinymce.init to the server by FTP etc when inserting it.
When you click the button of Prism plugin created by this, or select Prism from the menu item, the four languages Markup, css, C-like, JavaScript are displayed in the pull-down menu of the popup window.
Please enter the code you want to display with syntax highlighting in the text area displayed below it.
Also, when dragging a specific character string and clicking the button of the Prism plugin or selecting the Prism plugin of the menu item, the specific character string selected by dragging in the text area is automatically selected It is inserted.

Position the cursor over the string enclosed in the &lt;pre&gt;&lt;code class ="language-xx"&gt; ~~ &lt;/code&gt;&lt;/pre&gt; tag that is displayed as syntax highlighting in Prism, the Prism plugin The button of the button will flip.
By clicking the button in that state, you can erase the tag of &lt;pre&gt;&lt;code class="language-xx"&gt; ~~ &lt;/code&gt;&lt;/pre&gt;.
Please use it when you want to modify the tag, such as when you specify the wrong script language.
In addition, &lt;code&gt; ~~ &lt;/code&gt; tag which is not enclosed with &lt;pre&gt;&lt;/pre&gt; can also be deleted by clicking the button.


### How to specify the script language to be displayed in the plugin pull-down menu
Prism supports many scripting languages.
Since Prism can freely select and introduce those languages when installing it, I think that the language you want to display in the pull-down menu will differ depending on the usage situation of each person.
So in this plugin, enter the item prism_languages in tinymce.init and list the languages that Prism uses in the format \{text: 'xx', value: 'xx'\} in it By inserting it, you can display it in the Prism plugin.
If the item of prism_languages is not filled out, the four languages mentioned in the usage are displayed.

For example, if you want to display 7 languages such as Markup, JavaScript, css, PHP, SQL, Smarty, Ini in the pull-down menu, it is as follows.
<pre><code>prism_languages: [
	{text: 'HTML/XML',   value: 'markup'},
	{text: 'JavaScript', value: 'javascript'},
	{text: 'CSS',        value: 'css'},
	{text: 'PHP',        value: 'php'},
	{text: 'SQL',        value: 'sql'},
	{text: 'Smarty',     value: 'smarty'},
	{text: 'Ini',        value: 'ini'}
],</code></pre>
Please enter "xx" part of language-xx described in Supported languages of Prism's official website (https://prismjs.com/) in value:'' and please insert each language name into text: ''. Please enclose it with \{\} when inserting it.
Be sure to add comma after \{\} when writing more than one. However, as an exception there is no need to make the last line.
Please be aware that it will cause an error if you forget to insert it.

### How to hide the number of rows, specify the number of lines of the first line, or specify lines to emphasize
Prism allows you to make various displays by introducing a plugin.
This plugin is created assuming that Prism has introduced Line Numbers and Line Highlight.
You can choose to show / hide the number of lines by checking "Line Number" at the bottom of the pop-up window (By default, the number of lines is set).
"First Line" can specify the line number you want to put in the very first line. These two types use the function of Line Numbers.
"Highlight" is by using the function of the Line Highlight, you can specify the line you want to highlight. You can also use the method described on Prism's official website.
Also, if "Line Number" is not checked, even if data is inserted in "First Line" or "Highlight", those data will not be reflected in the inserted code. Therefore, it is designed so that "Line number display" is unchecked and at the same time, input area of "First Line" and "Highlight" is disabled.


### Attention
This plugin was created by trial and error by one person. Therefore, trouble may occur.

Damage caused by using this plugin is not responsible at all.


### How to delete a plugin
1. Delete the prism folder in the plugin folder included in the TinyMCE folder from the server.
2. Delete the prism character string described in tinymce.init 's plugins and toolbar, and if prism_languages is specified, delete the description of prism_languages: \[ ~~ \] and add the file containing tinymce.init Please upload it to the server.
