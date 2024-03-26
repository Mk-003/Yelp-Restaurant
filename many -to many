class Customer:
    def __init__(self, first_name, last_name):
        self.first_name = first_name
        self.last_name = last_name

    def reviews(self):
        self._reviews

    def restaurants(self):
        return {review.restaurant for review in self._reviews}

    def num_negative_reviews(self):
        return sum(1 for review in self._reviews if review.rating < 3)

    def has_reviewed_restaurant(self, restaurant):
        return any(review.restaurant == restaurant for review in self._reviews)
    
class Restaurant:
    def __init__(self, name):
        self.name = name
        self.reviews

    def reviews(self):
        self._reviews

    def customers(self):
        return {review.customer for review in self._reviews}

    def average_star_rating(self):
        return sum(review.rating for review in self._reviews) / len(self._reviews) if self._reviews else None

    @classmethod
    def top_two_restaurants(cls):
        
        all_reviews = [review for review in (rev for customer in Customer.all_customers() for rev in customer.reviews())]
        top_restaurants = []
        while len(top_restaurants) < 2:
            best_rating = 0
            best_restaurant = None
            for restaurant in Restaurant.all_restaurants():
                if restaurant not in top_restaurants:
                    avg_rating = restaurant.average_star_rating()
                    if avg_rating is not None and avg_rating > best_rating:
                        best_rating = avg_rating
                        best_restaurant = restaurant
            if best_restaurant is not None:
                top_restaurants.append(best_restaurant)

        return top_restaurants
    
class Review:
    def __init__(self, customer, restaurant, rating):

        if not isinstance(customer, Customer):
            raise ValueError("Customer must be a Customer object")
        if not isinstance(restaurant, Restaurant):
            raise ValueError("Restaurant must be a Restaurant object")
        if not isinstance(rating, int) or (rating < 1 or rating > 5):
            raise ValueError("Rating must be an integer between 1 and 5")

        self.customer = customer
        self.restaurant = restaurant
        self.rating = rating
