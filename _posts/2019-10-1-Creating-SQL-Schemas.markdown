---
layout: post
title: SQL Schemas
date: 2019-10-01
author: Mitchell R.
excerpt: "Creating SQL Schemas"
---

In lab 5, my professor gave the class this scenario:

<blockquote>An auction website has items for sale that are provided by sellers. Each item has an opening price, a description, and an ending time. Customers submit bids. The highest, earliest bid submitted before the ending time is the winning bid and the item is sold to the bidder. Each seller must pay the auction company 5% of the winning bid. The auction company wants to be able to analyze the sales behavior of its customers and sellers and so must keep track of all bids and sales.</blockquote>

We had to first begin by creating an entity relationship diagram in [Draw.io][draw]. This is mine.
<span class="image fit"><img src="{{ "/images/Draw.png" | absolute_url }}" alt="" /></span>

I first created 4 entities, the Auction Company, Sellers, Customers, and Items.
The relationship between sellers and items consists of putting them up for sale.
I assumed that each seller could have multiple items. The relationship between Customers
and items is a bid and a sale. I assumed that customers could many bids, and each item could
have many bids for it. The bid with the highest price and the most recent time would go to a sale.
Each item can only be sold once, and the sale goes to the auction company. The company then would
take their tax and give the rest to the seller.

I then had to create an SQLite schema of the same scenario using [Vertabelo][vert].
<span class="image fit"><img src="{{ "/images/Vertabelo.png" | absolute_url }}" alt="" /></span>

After I started to create this schema, I decided to change some of my relationships up.
Now the seller just has a reference to the items they are selling. The sales now have more information
regarding the bid for the items. The sale now also has a relationship to the auction company and the seller.
This should allow for the 5% tax to be shown in the auction company's table, and the rest in the
seller's table

I think my scheme is just ok. I wanted to have some sort of function that auto
calculates the percentage of the sale that went to each entity, but I wasn't able
to figure it out. I don't think the relationship being described in my scheme accurately shows
what I intended it to. I think that my other relationships do show the right thing.

[vert]: https://www.vertabelo.com/
[draw]: https://www.draw.io/
