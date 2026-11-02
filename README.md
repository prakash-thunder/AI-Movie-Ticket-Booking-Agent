# AI Movie Ticket Booking Agent 

A simple AI-powered movie booking assistant built with **Python, Hugging Face, LangChain, and LangGraph**. You can chat with it to choose a city, movie, showtime, and number of tickets. The assistant remembers your choices, checks the sample seat availability, and creates a **demo booking** after you confirm.

I built this project to learn how an AI agent can understand natural-language requests, use tools, and manage a multi-step conversation.

## Features

- Chat naturally to select a city and movie.
- View available showtimes, ticket prices, and remaining seat counts.
- Choose **1–6 tickets** and see the total cost.
- Review the details before confirming a booking.
- Get a unique **demo booking ID** after confirmation.
- Start a new booking without restarting the notebook.

## Tech stack

| Technology | Use |
| --- | --- |
| Python | Booking logic and sample show data |
| Hugging Face — Qwen2.5-1.5B-Instruct | Understands the user's messages |
| LangChain | Prompting, structured detail extraction, and booking tools |
| LangGraph | Controls the conversation steps and remembers selections |
| Google Colab | Runs the entire project in one notebook |

## How it works

```text
User message
     ↓
Hugging Face model extracts booking details
     ↓
LangGraph keeps track of city, movie, time, and tickets
     ↓
LangChain tools look up sample showtimes and seat counts
     ↓
Booking summary → User confirms → Demo booking ID
```

The project uses three simple LangChain tools: `list_movies`, `list_showtimes`, and `book_tickets`.

## Run in Google Colab

1. Download or open [`AI_Movie_Ticket_Booking_Agent_HuggingFace_LangChain_LangGraph_proj.ipynb`](AI_Movie_Ticket_Booking_Agent_HuggingFace_LangChain_LangGraph_proj.ipynb) in [Google Colab](https://colab.research.google.com/).
2. Go to **Runtime → Change runtime type** and select a **T4 GPU** if available.
3. Run the cells from top to bottom. The notebook installs the required packages and downloads the Hugging Face model.
4. Run the example conversation in **Section 7**, then try your own messages in **Section 8**.

**No paid API key or `.env` file is required.** The first model download may take a little time.

## Example conversation

```text
You: I want to watch a movie in Delhi
Agent: In Delhi, you can watch: Interstellar, Inception. Which movie would you like?

You: Interstellar
Agent: Available shows for Interstellar in Delhi: 6:00 PM (₹250, 12 seats left),
       9:00 PM (₹300, 10 seats left). Which time works for you?

You: 6:00 PM, 2 seats
Agent: Here's your booking summary:
       Movie: Interstellar
       City: Delhi
       Showtime: 6:00 PM
       Seats: 2
       Total: ₹500
       Type 'confirm' to make a DEMO booking.

You: confirm
Agent: Booking confirmed (demo only)! Your demo booking ID is generated.
```

*This conversation illustrates the intended flow. The exact wording and booking ID may vary.*

## Important note

This is a **learning prototype**, not a real cinema booking service. Movie titles, cities, showtimes, prices, and available seat **counts** are stored in a Python dictionary inside the notebook. There is **no live cinema API, individual seat map, payment system, or real ticket purchase**. Bookings and seat-count updates are stored only for the current Colab session.

## Future improvements

I plan to connect real cinema listing APIs where authorized, add individual seat selection, save bookings in a database, and build a simple Flask interface.
