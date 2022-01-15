10.1.7 Refactor the code to handle Random Potion Creation

        Remember, our Potion object is supposed to be one of three different types: health, agility, or strength.

        Eventually, once we write the game logic, we'll want our enemies to be able to drop a random potion. Because this logic is strictly related to a potion, we can go ahead and include it in the Potion() constructor. If the Potion() constructor is called without any arguments, we will have it create a new potion with a random type and value.

        Following the TDD cycle, let's write a failing test that will check for this. Update the Potion.test.js file with a second failing test, as shown in the following code:

        test('creates a random potion object', () => {
        const potion = new Potion();

        expect(potion.name).toEqual(expect.any(String));
        expect(potion.name.length).toBeGreaterThan(0);
        expect(potion.value).toEqual(expect.any(Number));
        });
        Note that this time, we won't check to see if the potion has the name value of health. If we wanted to, we could have written a test that checks to see if name is health, strength, or agility.

        Run npm run test to make sure that the test fails. The following image shows the output from a second test that fails:

        Screenshot of second test failing

        Now let's refactor the Potion() constructor to fulfill the failing test, as shown in the following code:

        function Potion(name) {
        this.types = ['strength', 'agility', 'health'];
        this.name = name || this.types[Math.floor(Math.random() * this.types.length)];

        if (this.name === 'health') {
            this.value = Math.floor(Math.random() * 10 + 30);
        } else {
            this.value = Math.floor(Math.random() * 5 + 7);
        }
        }

        module.exports = Potion;
        DEEP DIVE
        Now let's run our test one more time to make sure both tests still pass. The following image shows the output:

        Screenshot of potion tests passing

        Everything passed! Although this process may seem tedious, remember that this back-and-forth, test-then-refactor is the crux of TDD. You'll begin to appreciate the benefits of this workflow as we develop the more complex pieces of game logic.

        We won't be using the random.js module going forward, so you can delete that file and its corresponding test if you'd like. The important part is having a working Potion() constructor.

        Remember to save your progress with git add and git commit. You can also merge the feature branch into develop and close the GitHub issue.

        Nice job! Now it's time to check your knowledge by completing a quick assessment:

