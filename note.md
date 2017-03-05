# Module 2

## Assets

* Concatenate resources
  * into fewer separate resource files
  * requiring fewer connections

* Turmolinks turns a multi-page server-side application into a pseudo
  single-page application
  * reduce full page loads
  * remember app/view/layouts/application.html.erb

* Compress js and CSS source code into only what is necessary for the browser
* Potentially use a CDN (Content Distribution Network)
  * faster nerwork connecction and download times

* Gemfile:

```ruby
gem 'sass-rails', '~> 5.0', '>=3.4.22'
gem 'uglifier', '~> 3.0', '>=3.0.2'
gem 'coffee-rails', '~> 4.1', '>= 4.1.0'
gem 'jquery-rails', '~>4.2', '>=4.2.1'
```

```ruby
source 'https://rails-assets.org' do
  gem 'rails-assets-bootstrap', '~>3.3', '>= 3.3.7'
  gem 'rails-assets-angular', '~>1.5', '>= 1.5.8'
  gem 'rails-assets-angular-ui-router', '~>0.3', '>= 0.3.1'
  gem 'rails-assets-angular-resource', '~>1.5', '>= 1.5.8'
end
```

* `mkdir app/assets/stylesheets`
* `mkdir app/assets/javascript`
* create app/assets/stylesheets/spa-demo.css

```css
/*
 * SPA Demo Stylesheet Manifest File
 *
 *= require bootstrap
 */
```

* create app/assets/javascript/spa-demo.js

```js
//= require jquery2
//= require bootstrap
//= require angular
//= require angular-ui-router
//= require angular-resource
```

* create config/initializers/assets.rb :

```ruby
Rails.application.config.assets.version = '1.0'
Rails.application.config.assets.precompile += %w( spa-demo.js spa-demo.css )
```

* include assets in html app/views/ui/index.html.erb:

```erb
<%= stylesheet_link_tag    "spa-demo", :media => "all" %>
<%= javascript_include_tag "spa-demo" %>
```
