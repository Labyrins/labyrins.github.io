---
title: jekyll로 Github Page 만들기
cover-image: hipster.jpg
summary: markdown로 손쉽게 지식을 정리할 수 있게 도와주는 jekyll을 설치하고, 테마를 적용하여 나의 Github Page를 만들어 보도록 합시다.

---

Markdown문서로 문서를 작성하고, 이를 자동으로 정적인 페이지로 변환시켜주는 [Jekyll](https://jekyllrb-ko.github.io/)을 사용하여 손쉬운 블로그를 만들어 보도록 합시다. 이에 Gitbub Page는 Jekyll을 통해 서비스가 가능한 최고의 선택이 됩니다. Jekyll과 Github Page의 조합은 많은이들에게 사용된지 상당히 오래되었으므로, 본 포스팅에서는 현재의 페이지가 어떤 과정으로 생성되었는지에 대한 과정을 서술합니다.

[송성광님의 포스트](http://blog.saltfactory.net/upgrade-github-pages-dependency-versions/)를 참고하여 초기에 세팅을 진행했습니다. Ruby를 베이스로 한 Jekyll을 사용하기 위해서는 다양한 설정이 필요한데, 위의 포스팅은 초보자도 어려움 없이 맥에서 Jekyll환경을 세팅하기 위한 아주 자세한 설명이 담겨있습니다. 작성글대로 한다면 큰 어려움 없이 Github Page에 글을 작성하기 위한 준비를 하실 수 있을 것입니다.

Jekyll은 전세계 개발자들이 미리 만들어 놓은 좋은 테마를 무료(또는 유료?)로 사용이 가능합니다. [themes.jekyllrc.org](http://themes.jekyllrc.org/), [jekyllthemes.org](http://jekyllthemes.org/) 등을 통하여 본인의 취향에 맞는 테마를 선택하도록 합시다. 글쓴이는 [holo-alfa](http://steinvc.github.io/holo-alfa/)라는 단순하고 깔끔한 테마를 선택하여 진행을 하였습니다. `fork`를 떠서 본인의 repository에 옮긴뒤 약간의 커스터마이징을 가미하도록 합시다.

---
이로써 정적인 포스트를 작성하기 위한 모든 작업을 마쳤습니다. Jekyll에서의 포스트 작성은 기본적으로 Markdown의 문법을 사용하지만 Liquid를 사용한 확장표현이 가능합니다. 아래에는 Markdown의 기본문법을 벗어난 좀더 다양한 방법을 통한 사용예제를 소개합니다.

#### code snippet
아래와 같이 liquid에서 제공하는 `hilight`과 `endhilight`으로 코드를 감싸 표기할 수 있습니다.
{% highlight css %}
nav a:hover {
  color: rgba(0,0,0,.72);
}
nav a.current {
  color: rgba(0, 0, 0, .72)
}
.subtitle {
  margin: 30px 0;
}
{% endhighlight %}

#### 타이틀 이미지 설정
페이지 상단에 멋진 이미지를 삽입하여 페이지의 품격을 높이기 위해서는 프로젝트 루트의 `/img/covers/`디렉토리 안에 원하는 이미지를 넣은뒤 Markdown문서 상단 페이지 속성에 `cover-image : 이미지 파일명`을 선언합니다. 본 페이지 상단과 같이, 삽입된 이미지는 자동으로 하단으로 갈수록 이미지가 fadeout 됩니다.

#### 이미지 삽입
모든 이미지는 `img`디렉토리에서 관리합니다. 여타의 Markdown문법과 같이 사용하고, URL선언을 현재 프로젝트 내의 파일로 지정하면 손쉽게 이미지를 삽입할 수 있습니다. `site.baseurl`은 `_config.yml`에 선언되어 있음을 확인합시다. 출처를 명시할 때는 `<small></small>`를 사용합니다.

```
![Forest]({{ site.baseurl }}/img/howtoyoutubeimport.png)
```

#### 인용문 삽입
사용하려는 인용문을 `>`로 감싸 표기합니다. 이미지의 삽입과 마찬가지고 인용절 뒤에 `<small></small>`을 통해 출처 등을 남길 수 있습니다.

>It'll be nipper heaps trent from punchy oldies. Trent from punchy no dramas when flat out like a tucker-bag. He hasn't got a piker flamin frog in a sock.
><small>— [Bogan Ipsum](http://boganipsum.com/)</small>

#### Youtube 영상 삽입
Youtube영상을 삽입하기 위한 [FitVids.js](http://fitvidsjs.com/)가 추가되어 있습니다. `iframe`을 사용하여 삽입을 합니다. 아래와 같이 유튜브 영상페이지로부터 삽입할 소스코드는 손쉽게 구할 수 있습니다.

![Forest]({{ site.baseurl }}/img/howtoyoutubeimport.png)

<iframe width="560" height="315" src="https://www.youtube.com/embed/i1n_1jrUEjU" frameborder="0" allowfullscreen></iframe>

#### Tables 삽입

Table의 삽입은 [Github-Flavored-Markdown](https://help.github.com/articles/github-flavored-markdown/#tables)에 기반한 Markdown문법을 사용합니다. 자세한 문법은 위의 링크를 참고바랍니다.

```
| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |
```

| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |


이로써 페이지의 Jekyll - Github Page를 통한 블로그 준비와 포스트 작성에 관한 모든 것이 정리 되었습니다. 이제 지식을 쌓기만 하면 됩니다. 강철의 근성이 공부를 하는 여러분들에게 가호를 내리기 바라며..