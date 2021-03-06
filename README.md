# Crowdtilt API Ruby Client

An extremely light-weight ruby-based http client for the Crowdtilt API

For the latest information on this project, take a look at:

* [This project's source code repo](https://github.com/msaint/crowdtilt)
* [The Crowdtilt API documentation](https://github.com/Crowdtilt/crowdtilt-api-spec)

##Usage Examples##

###Including the gem in your Gemfile###

    gem 'crowdtilt', :github => 'msaint/crowdtilt'


###Initializing the client###
Your api_key / api_secret is required to initialize the client.  Please email [support.api@crowdtilt.com](mailto: support.api@crowdtilt.com) to request credentials.

You should specify with the `mode` parameter whether you are attempting to access the `sandbox` API or the `production` API.

    Crowdtilt.configure :api_key => YOUR_API_KEY, 
                        :api_secret => YOUR_API_SECRET, 
                        :mode => API_MODE   # 'sandbox' or 'production'

###Calling API methods###
See [Crowdtilt's API documentation](https://github.com/Crowdtilt/crowdtilt-api-spec) for more information about the list of available client methods.  Methods are called by simply passing in the URI of the resource you are accessing, along with any needed parameters as a hash object.

The response is returned as a hash.

Errors returned by the API will be raised as exceptions.

**Examples:**

Create a user:
    
    user = {
      :firstname => 'John',
      :lastname => 'Smith',
      :email => 'js@example.com'
    }
        
    response = Crowdtilt.post('/v1/users', { :user => user })

Get a list of users:

    response = Crowdtilt.get('/v1/users')
    
Update a user:

    user_update = { :email => 'newemail@example.com' }

    response = Crowdtilt.put('/v1/users/USR123', { :user => user_update })
