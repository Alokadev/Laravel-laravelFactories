# Laravel-laravelFactories
How to set simple laravel factory

# Command for factory
php artisan make:factory TicketFactory --model=Ticket

# TicketFactory
<?php

namespace Database\Factories;

use App\Models\Ticket;
use Illuminate\Database\Eloquent\Factories\Factory;

class TicketFactory extends Factory
{
    /**
     * Define the model's default state.
     *
     * @return array
     */
    public function definition()
    {
        return [
            'customer_name' => $this->faker->name(),
            'email' => $this->faker->email(),
            'phone' => $this->faker->phoneNumber(),
            'description' => $this->faker->text(30),
        ];
    }
}

# DatabaseSeeder

<?php

namespace Database\Seeders;

use App\Models\Ticket;
use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        // Seed 10 fake tickets
        Ticket::factory()->count(10)->create();
    }
}

# However at the end TicketFactory changes as below

<?php

namespace Database\Factories;

use App\Models\Ticket;
use Illuminate\Database\Eloquent\Factories\Factory;
use Illuminate\Support\Str;

class TicketFactory extends Factory
{
    /**
     * Define the model's default state.
     *
     * @return array
     */
    public function definition()
    {
        return [
            'customer_name' => $this->faker->name(),
            'email' => $this->faker->email(),
            'phone' => $this->faker->phoneNumber(),
            'description' => $this->faker->text(30),
            'ref' => Str::uuid(), // Generate a UUID
            'status' => 0, // Set status to 0
        ];
    }
}






