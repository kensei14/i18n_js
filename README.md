https://github.com/fnando/i18n-jsのサンプル

①gem install i18n-js

②rake i18n:js:setup

i18-js.ymlファイルの生成。初期化（？）

③rake i18n:js:export

/config/locale以下の翻訳YAMLファイルの内容をJSのファイルへ。

＊初期設定では全てのYAMLファイルの内容をまとめてapp/assets/javascripts/i18n/translations.jsに格納される。config/i18n-js.yml内の設定で言語毎に分割できたりする。

	translations:
	- file: "app/assets/javascripts/i18n/translations.js"
	
	- file: "app/assets/javascripts/i18n/jslang.js"
	  only: "*.js"   

④i18n.js内のI18nオブジェクトにlocaleを設定。localeをもとに翻訳される。

	<script type="text/javascript">
        I18n.defaultLocale = "<%= I18n.default_locale %>";
        I18n.locale = "<%= I18n.locale %>";
        I18n.fallbacks = true;
                 
    	alert("標準のロケールは" + I18n.locale);
    </script>
    
⑤I18n.translate('en.hello');

localeに合わせた’こんにちは’が出てくる。

	alert(I18n.t('js.hello'));
    alert(I18n.t('js.goodbye'));