# Django
**:book: Contents**
- [Django](#Django)
    - [MTV 패턴](#MTV-패턴)
    - [Django ORM](#Django-ORM)
    - [admin site](#admin-site)
    - [Middleware](#Middleware)
    - [settings.py](#settings.py)
    - [migrations](#migrations)
    - [URL 라우팅](#URL-라우팅)
    - [보안 기능](#보안-기능)
    - [쿼리 최적화](#쿼리-최적화)
    - [Static 파일과 Media 파일](#Static-파일과-Media-파일)


---

### MTV 패턴
* Django는 MVC 패턴의 변형인 MTV(Model-Template-View) 패턴을 사용합니다. 여기서:
    * Model: 데이터베이스의 구조와 데이터를 관리하는 부분으로, Django ORM(Object-Relational Mapping)을 통해 정의됩니다.
    * Template: 사용자에게 보여지는 프런트엔드 부분으로, HTML 파일에 Django 템플릿 언어를 사용하여 데이터를 동적으로 표시합니다.
    * View: 비즈니스 로직과 요청에 따라 반환할 데이터를 결정하는 부분입니다. 이곳에서 데이터를 가져와 템플릿에 전달합니다.

### Django ORM
* Django ORM은 데이터베이스와 상호작용하기 위한 추상화된 API입니다. 장점으로는:
    * SQL 문을 작성하지 않고도 데이터베이스 작업을 수행할 수 있습니다.
    * 다중 데이터베이스 지원, 데이터베이스 간 이동 용이성.
    * 개발자가 데이터베이스의 특정 구현에 의존하지 않고 코드 작성 가능.

### admin site
* Django는 자동으로 웹 기반 관리자 인터페이스를 생성하는 admin 사이트를 제공합니다. admin.py 파일에서 모델을 등록하여 관리할 수 있으며, 관리자 페이지에서 모델 데이터를 생성, 읽기, 수정, 삭제(CRUD)할 수 있습니다. 이를 통해 관리 인터페이스를 매우 간단하게 설정할 수 있습니다.

### Middleware
* Middleware는 요청(request)와 응답(response) 처리 과정에서 실행되는 후킹(hooking) 시스템입니다. 각 미들웨어는 요청과 응답을 처리하거나 변형할 수 있습니다. 예를 들어, 인증, 캐싱, 세션 관리, 사용자 로케일 설정 등이 미들웨어에서 처리될 수 있습니다.

### settings.py
* settings.py 파일은 Django 프로젝트의 모든 설정을 정의하는 곳입니다. 여기에는 데이터베이스 설정, 설치된 애플리케이션 목록, 미들웨어, 템플릿 경로, 정적 파일 설정, 로깅 설정 등이 포함됩니다. 이를 통해 Django 프로젝트의 환경을 쉽게 구성할 수 있습니다.

### migrations
* Migrations는 Django에서 모델에 대한 변경 사항을 데이터베이스 스키마로 반영하기 위한 방법입니다. 이를 통해 데이터베이스를 유지 관리하고, 데이터 손실 없이 모델의 변경 사항을 관리할 수 있습니다. makemigrations 명령으로 새로운 마이그레이션을 생성하고, migrate 명령으로 이를 데이터베이스에 적용합니다.

### URL 라우팅
* Django의 URL 라우팅은 urls.py 파일에서 이루어집니다. 각 URL 패턴은 특정 뷰(view) 함수나 클래스에 매핑됩니다. URL 패턴은 정규 표현식을 사용하여 정의할 수 있으며, 이를 통해 다양한 URL 요청을 처리할 수 있습니다. Django 2.0 이후부터는 path()와 re_path() 함수를 사용하여 URL 패턴을 정의합니다.

### 보안 기능
* Django는 기본적으로 여러 보안 기능을 제공합니다.
    * CSRF 보호: CSRF(Cross-Site Request Forgery) 공격을 방지하기 위한 토큰 기반 보호.
    * XSS 방지: 템플릿 엔진에서 HTML을 자동으로 이스케이프하여 XSS(Cross-Site Scripting) 공격을 방지.
    * SQL 인젝션 방지: Django ORM을 사용하여 SQL 인젝션 공격을 방지.
    * 보안 설정: SECURE_SSL_REDIRECT, SECURE_HSTS_SECONDS와 같은 설정을 통해 HTTPS를 강제하고 보안을 강화할 수 있습니다.

### 쿼리 최적화
* 쿼리 최적화는 성능 향상을 위해 중요합니다.
    * Select Related: 외래 키 또는 일대일 관계에 대해 select_related()를 사용하여 쿼리 수를 줄임.
    * Prefetch Related: 다대다 또는 외래 키 관계에 대해 prefetch_related()를 사용하여 쿼리 수를 줄임.
    * Indexing: 데이터베이스 테이블에 인덱스를 추가하여 검색 속도를 높임.
    * QuerySet Caching: 동일한 쿼리를 반복해서 호출하는 것을 방지하기 위해 쿼리셋을 캐싱하여 사용.

### Static 파일과 Media 파일
* Static 파일: CSS, JavaScript, 이미지 등 정적 파일을 관리합니다. STATIC_URL, STATICFILES_DIRS, STATIC_ROOT 등의 설정을 통해 정적 파일을 처리하고 배포할 수 있습니다.
* Media 파일: 사용자 업로드 파일(이미지, 문서 등)을 관리합니다. MEDIA_URL과 MEDIA_ROOT 설정을 통해 미디어 파일의 저장 경로와 URL을 설정할 수 있습니다.
