Controller specs live in `spec/controllers` or any example group with
`:type => :controller`.

A controller spec is an RSpec wrapper for a Rails functional test
(ActionController::TestCase::Behavior).  It allows you to simulate a single
http request in each example, and then specify expected outcomes, including:

* templates that are rendered by the action
* instance variables that are assigned in the controller to be shared with the
  view
* cookies that get sent back with the response

To specify outcomes, you can use:
    
* standard rspec matchers (`response.code.should eq(200)`)
* standard test/unit assertions (`assert_equal 200, response.code`)
* rails assertions (`assert_response 200`)
* rails-specific matchers:
  * `response.should render_template (wraps assert_template)`
  * `response.should redirect_to (wraps assert_redirected_to)`
  * `assigns(:widget).should be_a_new(Widget)`
    
## Conventions:

### Controller

* pass the controller being specified to the outermost `describe` method.

      describe AccountController do
        # ...

### Views

* by default, views are not rendered. See
  [views are stubbed by default](controller-specs/views-are-stubbed-by-default) and
  [render_views](controller-specs/render-views) for details.
