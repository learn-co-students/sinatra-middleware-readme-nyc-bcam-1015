# Sinatra Middleware

### What is Sinatra Middleware?

Sinatra is built on top of Rack. As a result, Sinatra utilizes Rack's middleware that we learned about earlier. Middleware are essentially components that sit between the server and your application, monitoring and/or manipulating the HTTP requests/responses in order to provide functionality. For example, if I wanted to include a testing component via middleware, I could require a file called `testing_component`, and specify for it to be used in my Sinatra application.

### How does this work?

Sinatra makes it quite easy to build out a middleware pipeline via the `use` method inside of our `config.ru` file:

```ruby
require 'sinatra'
require 'testing_component'

use Rack::Lint
use TestingComponent
```

The `require 'testing_component'` line will require the ruby file that has the middleware component code, and correspondingly makes it available to us inside `config.ru`. Then we specify the `use TestingComponent` line in order to mount the `TestingComponent` class in our app's middleware pipeline.

### Why is this important?

Rack is distributed with middleware components out of the box. These components are used for logging, debugging, routing, sessions, authentication, testing, and so on. Sinatra uses a large number of these middleware components by default. You can find a long list of middleware components [here](https://github.com/rack/rack/wiki/List-of-Middleware).

### Resources
- [List of Middleware](https://github.com/rack/rack/wiki/List-of-Middleware)
