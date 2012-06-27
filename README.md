# Plant

Plant is used to seed your project with data.

---

## Getting started

 1. Add the `plant` bundle to *bundles.php*
 2. Create a `seeds` folder in your application directory.
 3. Create seed files. For example:

        <?php // file: /application/seeds/users.php

        class Seed_Users extends \S2\Seed {

            public function grow()
            {
                $user = new User;
                $user->username = 'johndoe';
                $user->password = '12345678';
                $user->save();

                $user = new User;
                $user->username = 'janedoe';
                $user->password = '12345678';
                $user->save();
            }

            // This is optional. It lets you specify the order each seed is grown.
            // Seeds with a lower number are grown first.
            public function order()
            {
                return 100;
            }

        }

---

## Growing Seeds

### All at once
run `artisan plant::seed all`

#### Excluding seeds
You can exclude specific seeds from being grown by using the `--not` option.
Separate multiple exclusions with a comma.

`artisan plant::seed all --not=users,posts`


### Individual seeds (e.g. users)
run `artisan plant::seed users`

 > If multiple seeds with the same filename exist, they will all be grown.
 > This could happen when seeds are stored in bundles.
 > e.g. **application/seeds/users.php** and **bundles/plant/seeds/users.php**
 >
 > *Sort orders are still used.*

### Controlling the order that seeds are grown
Each seed class may contain an `order()` method that returns a sort order integer.
Seeds with a lower sort order are grown first.