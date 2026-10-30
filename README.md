# SkyLine ✈️

An airline management web app. A Node.js / Express REST API backed by PostgreSQL, with a plain HTML/CSS/JavaScript front end for managing flights, passengers, bookings, payments, crews, baggage and feedback, plus revenue and destination reports.

## Features
- Staff login with session-based authentication
- CRUD APIs for flights, bookings, passengers, payments, aircraft, airlines, airports, airport crew, flight crew, baggage and feedback
- Reports built on database views: flight revenue, airline revenue, popular destinations and airline feedback summary
- Front-end pages for booking, flights, passengers, crew, feedback, destinations and revenue

## Tech stack
Node.js · Express · PostgreSQL (`pg`) · express-session · dotenv · HTML/CSS/JS

## Getting started
1. Install [Node.js](https://nodejs.org) and [PostgreSQL](https://www.postgresql.org).
2. Create a database named `SkyLine` and import its schema (tables, views and a `login` table).
3. Install dependencies: `npm install`
4. Copy `.env.example` to `.env` and fill in your database details.
5. Start the API: `npm start` (runs on http://localhost:5900)
6. Open `BackEnd/src/login.html` / `home.html` with a local server (e.g. VS Code Live Server).

## API overview
| Route | Purpose |
|---|---|
| `/flights`, `/booking`, `/payment`, `/baggage` | Flight, booking, payment and baggage records |
| `/passenger`, `/feedback` | Passengers and feedback |
| `/aircraft`, `/airline`, `/airport` | Fleet, airlines, airports |
| `/airportcrew`, `/flightcrew` | Crew management |
| `/revenue/flight-revenue`, `/revenue/airline-revenue` | Revenue reports |
| `/destination`, `/feedview` | Top destinations and feedback summary (`views.js`, port 3000) |

## Project structure
```
BackEnd/src/
  index.js        main API server
  views.js        secondary server for report views
  db.js           PostgreSQL connection (reads .env)
  routes/         one file per resource
  *.html, *.css   login and home pages
  FrontEnd/       feature pages and images
```

## Notes
Never commit your `.env` file. Passwords are currently stored and compared in plain text in the `login` table; hashing them with `bcrypt` is a planned improvement.
