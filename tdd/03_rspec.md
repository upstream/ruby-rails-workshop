!SLIDE
# RSpec
  * Erweitertes Test::Unit
  * eingebautes stubbing/mocking
  * Testing-DSL

.notes NEXT: beispiel

!SLIDE

    @@@ ruby
    describe Calculator, '#calculate' do
      before(:each) do
      end

      after(:each) do
      end

      it 'does something' do
        ...
      end
    end

.notes NEXT: matcher bsps

!SLIDE

# Matcher
    @@@ ruby
    .should == 'x'
    .should be_nil # .nil?
    .should be_a(String)
    .should have(3).items

.notes NEXT: mocking bsps

!SLIDE

# Mocking

    @@@ ruby
    .should_receive(:calculate).with('3+3')
    .should_receive(:calculate).with(anything)
    .should_receive(:calculate) {3}

.notes NEXT: should raise_error

!SLIDE

# Mocking

    @@@ ruby
    lambda {
      ...
    }.should raise_error(RuntimeError)

.notes NEXT: mocking bsp block

!SLIDE

# Mocking

    @@@ ruby
    .should_receive(:x).with do |arg1|
      arg1 == true
    end

.notes NEXT: rspec-rails

!SLIDE

# RSpec-Rails

!SLIDE

    @@@ ruby
    describe CalculatorsController, 'show' do
      it 'instantiates a calculator' do
        Calculator.should_receive(:new)

        get :show, term: '3+3'
      end

.notes NEXT: more code

!SLIDE

      @@@ ruby
      it 'calculates the term' do
        calculator = stub(:calculator)
        Calculator.stub(:new) {calculator}

        calculator.should_receive(
          :calculate).with('3+3')

        get :show, term: '3+3'
      end

.notes NEXT: more code

!SLIDE

    @@@ ruby
      it 'assigns the result' do
        Calculator.stub(:new) {
          stub(:calculate, calculate: 9)}

        get :show, term: '3+3'

        assigns(:result).should == 9
      end
    end

.notes rendert keine views. NEXT: uebung
