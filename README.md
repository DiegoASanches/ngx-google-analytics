# Ngx Google Analytics

An easy implementation to track ga on angular6+ apps.

**@TODO:** 
* Create service wrapper to ga commands;
* Create an Ng Router Helper;
* Create unit tests;

## Install

```
npm install ngx-google-analytics
```

## Feedbacks

https://github.com/maxandriani/ngx-google-analytics

## Simple Configuration

```ts
import { NgxGoogleAnalyticsModule } from 'ngx-google-analytics';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    NgxGoogleAnalyticsModule.forRoot('traking-code')
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

## Call GA Events

```ts
import { Component } from '@angular/core';
import { GoogleAnalyticsService } from 'ngx-google-analytics';

@Component( ... )
export class TestFormComponent {

  constructor(
    protected $gaService: GoogleAnalyticsService
  ) {}

  onUserInputName() {
    ...
    this.$gaService.event('enter_name', 'user_register_form', 'Name');
  }

  onUserInputEmail() {
    ...
    this.$gaService.event('enter_email', 'user_register_form', 'Email');
  }

  onSubmit() {
    ...
    this.$gaService.event('submit', 'user_register_form', 'Enviar');
  }

}
```

## Call GA Page Views and Virtual Page Views

```ts
import { Component, OnInit } from '@angular/core';
import { GoogleAnalyticsService } from 'ngx-google-analytics';

@Component(...)
export class TestPageComponent implements OnInit {

  constructor(
    protected $gaService: GoogleAnalyticsService
  ) {}

  ngOnInit() {
    this.$gaService.pageView('/teste', 'Teste de Title')
  }

  onUserLogin() {
    ...
    this.$gaService.pageView('/teste', 'Teste de Title', undefined, {
      user_id: 'my-user-id'
    })
  }

}
```