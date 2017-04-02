FORMAT: 1A

# Recipes

Recipes is a simple API allowing cooks to create, view, edit, and delete recipes from a collection.

# Group Recipes

Resources related to recipes in the API.

## Recipe Collection [/api/recipes]

### List All Recipes [GET]

+ Response 200 (application/json)

          [
            {
              "id": 3,
              "name": "Pecan Pie",
              "author": "Jean Wilson",
              "ingredients": [
                "3 eggs",
                "1 c. white sugar",
                "dash salt",
                "1 tsp. vanilla",
                "1/2 c. dark Karo syrup"
              ],
              "directions": "Melt 6 Tbsp. butter, mix in. Add 1 c. chopped nuts. Bake 57 mins. at 325 or 350."
            },
            {
              "id": 6,
              "name": "Sausage Balls",
              "author": "Jean Wilson",
              "ingredients": [
                "3 c. Bisquick",
                "1 lb. sausage",
                "8 oz.grated sharp cheddar"
              ],
              "directions": "Mix. Cook at 375 for 18 minutes."
            },
            {
              "id": 2,
              "name": "English Toffee",
              "author": "Gensie Johnston",
              "ingredients": [
                "2 c. chopped blanched almonds",
                "1 box light brown sugar (1 lb.)",
                "7 or 8 milk chocolate Hershey bars",
                "1 lb. butter (no substitute, please)"
              ],
              "directions": "Spread half of the nuts over the bottom of a lightly buttered cookie sheet. Combine brown sugar and butter in a medium sized heavy saucepan or skillet. Bring to a rolling boil, stirring constantly. Boil to hard crack stage (290 degrees or a little higher). Pour over the chopped nuts on the cookie sheet. Cover with the milk chocolate Hersheys and let them melt. Spread with a knife or spatula then top with the rest of the chopped nuts. Let get completely cold and crack apart. This is our traditional Christmas gift to our friends."
            }
          ]

### Create a New Recipe [POST]

You may create your own recipe using this action. It takes a JSON object
containing a recipe name, author name, list of ingredients, and directions.

+ name (string) - The name of the recipe
+ author (string) - The author of the recipe
+ ingredients (array[string]) - A collection of ingredients for the recipe
+ directions (string) - How to make the recipe

+ Request (application/json)

            {
              "name": "Candy",
              "author": "Iron Chef",
              "ingredients": [
                "2 c. chopped blanched almonds",
                "1 box light brown sugar (1 lb.)",
                "7 or 8 milk chocolate Hershey bars",
                "1 lb. butter"
              ],
              "directions": "Mix it all together and bake at 400 for 1 hour."
            }

+ Response 201 (application/json)

    + Body

                {
                  "id": 42
                  "name": "Candy",
                  "author": "Iron Chef",
                  "ingredients": [
                    "2 c. chopped blanched almonds",
                    "1 box light brown sugar (1 lb.)",
                    "7 or 8 milk chocolate Hershey bars",
                    "1 lb. butter"
                  ],
                  "directions": "Mix it all together and bake at 400 for 1 hour."
                }

## Recipe [/api/recipes/{recipe_id}]

+ Parameters
    + recipe_id (number) - ID of the Recipe in the form of an integer

### View a Recipe's Detail [GET]

+ Response 200 (application/json)

            {
              "id": 3,
              "name": "Pecan Pie",
              "author": "Jean Wilson",
              "ingredients": [
                "3 eggs",
                "1 c. white sugar",
                "dash salt",
                "1 tsp. vanilla",
                "1/2 c. dark Karo syrup"
              ],
              "directions": "Melt 6 Tbsp. butter, mix in. Add 1 c. chopped nuts. Bake 57 mins. at 325 or 350."
            }

### Update a Recipe's Detail [PUT]

+ Request (application/json)

            {
              "id": 3,
              "name": "Pecan Pie",
              "author": "Jean Wilson",
              "ingredients": [
                "4 eggs",
                "2 c. white sugar",
                "dash salt",
                "2 tsp. vanilla",
                "1 c. dark Karo syrup"
              ],
              "directions": "Melt 12 Tbsp. butter, mix in. Add 2 c. chopped nuts. Bake 57 mins. at 325 or 350."
            }

+ Response 200 (application/json)

            {
              "id": 3,
              "name": "Pecan Pie",
              "author": "Jean Wilson",
              "ingredients": [
                "4 eggs",
                "2 c. white sugar",
                "dash salt",
                "2 tsp. vanilla",
                "1 c. dark Karo syrup"
              ],
              "directions": "Melt 12 Tbsp. butter, mix in. Add 2 c. chopped nuts. Bake 57 mins. at 325 or 350."
            }

### Partially Update a Recipe's Detail [PATCH]

+ Request (application/json)

            {
              "ingredients": [
                "4 eggs",
                "2 c. white sugar",
                "dash salt",
                "2 tsp. vanilla",
                "1 c. dark Karo syrup"
              ],
              "directions": "Melt 12 Tbsp. butter, mix in. Add 2 c. chopped nuts. Bake 57 mins. at 325 or 350."
            }

+ Response 200 (application/json)

            {
              "id": 3,
              "name": "Pecan Pie",
              "author": "Jean Wilson",
              "ingredients": [
                "4 eggs",
                "2 c. white sugar",
                "dash salt",
                "2 tsp. vanilla",
                "1 c. dark Karo syrup"
              ],
              "directions": "Melt 12 Tbsp. butter, mix in. Add 2 c. chopped nuts. Bake 57 mins. at 325 or 350."
            }

### Delete [DELETE]

+ Response 204
