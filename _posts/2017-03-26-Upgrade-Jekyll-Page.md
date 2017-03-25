---
title: Jekyll Page에 기능 추가하기
summary: 너무 밋밋하고 피드백없는 정적인 페이지에 몇개의 기능을 추가하고 있습니다.
---

Markdown 형태의 정적인 페이지가 너무 밋밋하고 피드백을 받을 수 있는 영역이 없을 뿐더러 나중에 글이 늘어나면 포스트 관리의 어려움도 걱정되는 터라 몇개의 기능을 추가해보려 합니다.

#### 페이스북 소셜플러그인 - 댓글기능 추가

페이지 하단의 페이스북 댓글 창을 추가하기 위해서 해야할 작업은 그리 어렵지 않습니다. 우선 [페이스북 개발자 소셜 플러그인 패아자](https://developers.facebook.com/docs/plugins/comments/#configurator)내의 "댓글 플러그인 코드 생성 도구"를 통해 쉽게 코드를 얻어올 수 있습니다. `url`항목은 어차피 Liquid태그로 수정을 해야하니 대충 넣고, `너비`는 Responsive한 웹을 위해 100%, `게시물` 수는 입맛에 맞게 넣습니다. 저는 default로 되어 있는 '5'를 사용했습니다. 3개의 항목을 채우고 해당 서식 바로 아래 있는 `코드받기`를 통해 두개의 코드를 받아옵니다. 

{% highlight html %}
<div id="fb-root"></div>
<script>(function(d, s, id) {
  var js, fjs = d.getElementsByTagName(s)[0];
  if (d.getElementById(id)) return;
  js = d.createElement(s); js.id = id;
  js.src = "//connect.facebook.net/ko_KR/sdk.js#xfbml=1&version=v2.8";
  fjs.parentNode.insertBefore(js, fjs);
}(document, 'script', 'facebook-jssdk'));</script>
{% endhighlight %}

첫번째의 코드는 페이지내의 `<body>`태그 바로 뒤에 붙이라고 가이드가 되어 있습니다. 그렇다면 우리는 `_layout/default.html`의 `<body>`태그 뒤에 바로 붙여줍니다. 그리고 두번째로 주어지는 페이스북 댓글창으로 사용될 코드인데, 댓글은 각 페이지의 주소마다 다르게 보여집니다. 따라서 `data-href`의 값으로 고정주소를 선언하게 되면 블로그내의 모든 포스팅에서 모두 동일한 페이스북 댓글창을 사용하게 됩니다. 따라서 Liquid문법을 이용하여 현재 페이지의 url을 동적으로 생성하고 이렇게 만든 두번째 html코드를 `_include/post.html`에사용하도록 합니다. 

{% highlight html %}
<div class="fb-comments" 
     data-href={{ "{{ site.url | append: page.url "}}}}
     width="100%" 
     data-numposts="5" ></div>
{% endhighlight %}

웹에서의 페이스북 소셜플러그인 댓글 기능의 사용은 별도의 App-id가 필요없이 현재 포스트에 대한 url을 해당 `data-href`에 어떻게 지정할지만 고민을 하면 아주 손쉽게 붙일 수 있습니다.

---

#### TAG 기능

TBD