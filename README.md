# rubocop-sh
When you want to run rubocop, but it's not installed, this will install the required ruby gems.

My first bash script.  Any tips or suggestions are welcomed and appreciated.

#### 1) Add this to your ~/.bash_profile
    # -------
    # rubocop
    # -------
    # example usage:
    #   check a directory:     rubocop app/controllers
    #   check a file:          rubocop app/controllers/    application_controller.rb
    #   check rspec directory: rubycop spec/controllers
    #   check rspec file:      rubycop spec/controllers/application_controller_spec.rb
    run_rubocop(){
      if gem list | gem list | grep 'rubocop\|rubocop-rspec' ; then
        echo "rubycop and rubocop-rspec gems already installed"
        echo "* Running rubocop"
        rubocop --require rubocop-rspec $@
      else
        echo "* Installing required ruby gems"
        gem install rubocop --no-ri --no-rdoc
        gem install rubocop-rspec --no-ri --no-rdoc
        echo "* Running rubocop"
        rubocop --require rubocop-rspec $@
      fi
    }
    alias rubocop='run_rubocop $@'

#### 2) Reload your session with the updated .bash_profile
    source ~/.bash_profile
