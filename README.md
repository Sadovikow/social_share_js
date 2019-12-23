# social_share_js

Шаринг в соцсетях. Код максимально минимизирован.

### HTML

```html
<a onclick="Share.vkontakte('URL','TITLE','IMG_PATH','DESC')">Вконтакте</a>
<a onclick="Share.facebook('URL')">Facebook</a>
<a onclick="Share.mailru('URL','TITLE','IMG_PATH','DESC')">Mail.ru</a>
<a onclick="Share.odnoklassniki('URL','DESC')">Одноклассники</a>
<a onclick="Share.twitter('URL','TITLE')">Twitter</a>
<a onclick="Share.pintirest('URL','IMG_PATH','TITLE')">Pintirest</a>
<a onclick="Share.whatsapp('URL','TEXT')">Whatsapp</a>
```

### JS
```js
Share = {
	vkontakte: function(purl, ptitle, pimg, text) {
		url  = 'http://vkontakte.ru/share.php?';
		url += 'url='          + encodeURIComponent(purl);
		url += '&title='       + encodeURIComponent(ptitle);
		url += '&description=' + encodeURIComponent(text);
		url += '&image='       + encodeURIComponent(pimg);
		url += '&noparse=true';
		Share.popup(url);
	},
	odnoklassniki: function(purl, text) {
		url  = 'http://www.odnoklassniki.ru/dk?st.cmd=addShare&st.s=1';
		url += '&st.comments=' + encodeURIComponent(text);
		url += '&st._surl='    + encodeURIComponent(purl);
		Share.popup(url);
	},
	facebook: function(purl) {
      	 url = 'http://www.facebook.com/sharer.php?s=100';
         url += '&u=' + encodeURIComponent(purl);
        Share.popup(url);
		Share.popup(url);
	},
	twitter: function(purl, ptitle) {
		url  = 'http://twitter.com/share?';
		url += 'text='      + encodeURIComponent(ptitle);
		url += '&url='      + encodeURIComponent(purl);
		url += '&counturl=' + encodeURIComponent(purl);
		Share.popup(url);
	},
	mailru: function(purl, ptitle, pimg, text) {
		url  = 'http://connect.mail.ru/share?';
		url += 'url='          + encodeURIComponent(purl);
		url += '&title='       + encodeURIComponent(ptitle);
		url += '&description=' + encodeURIComponent(text);
		url += '&imageurl='    + encodeURIComponent(pimg);
		Share.popup(url)
	},
	pintirest: function(purl, pimage, description) {
        url  = 'https://pinterest.com/pin/create/button/?';
        url += 'url='          + encodeURIComponent(purl);
        url += '&media='       + encodeURIComponent(pimage);
        url += '&description=' + encodeURIComponent(description);
        Share.popup(url);
    },
    whatsapp: function (purl, text) {
        url = 'https://api.whatsapp.com/send';
        url += '?text=' + encodeURIComponent(text);
        url += ' | ' + encodeURIComponent(purl);
        Share.popup(url)
    },

	popup: function(url) {
		window.open(url,'','toolbar=0,status=0,width=626,height=436');
	}
};
```


*Данное решение является самым минималистичным из мною встречаемых, с свободной кастомизацией внешнего вида. Оно избавляет от надобности в использовании сторонних сервисов типа pluso.ru и дает возможность вести собственную статистику на своем же сервере.*
