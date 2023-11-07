# What’s the problem with carbon-aware software then?

Let’s turn to exploring how the grid works in conjunction with the current carbon-aware software patterns.

Up until now, carbon-aware software techniques have been focused on the opportunities presented by changing fuel mixes on the supply side. As we’ve seen above, effective grid management is about maintaining an equilibrium. Messing with that balance has consequences, and for the most part the impacts result in increased carbon emissions.

## ⏱ Applying the realities of grid management to “carbon-aware” time-shifting

> Quick reference – Time-shifting compute 
>
> Looking for the time of day when electricity will be greenest e.g. when there are fewest fossil-fuels in the energy mix, and setting compute jobs to run at that time. This means that the time of day the jobs run is dynamic and frequently changes.

Let's use a simple example to illustrate this concept. Say that you run a single, scheduled database backup job every day. You decide to change the scheduled time of running that task depending on the grid mix for a given day. The electricity to run this compute will already be factored into your grid’s daily electricity demand planning.

Now, say that over the course of a day, your local grid produces 100 tons of CO2 through generating the electricity it supplies. And, over the course of a day, your local grid supplies electricity with the following mix:

| **Time of day** | **Expected demand** | **Fossil Fuel Mix** | **Renewables Mix** |
| --- | ----------- | --- | ----------- |
| Morning | Low | 80% | 20% |
| Afternoon | High | 50% | 50% |
| Night | Low | 80% | 20% |

Remember that the grid has already planned for all its expected demand for that day. Based on this it produces electricity that generates 100 tons of CO2. Therefore whenever you choose to run your backup job, 100 tons of CO2 will still be generated by the grid for that day. 

Changing the timing of your job to run during the afternoon, when the mix of renewables is highest, doesn't actually change the day's emissions. By running your regular compute job during that renewable window, you have merely displaced the days’ emissions, not reduced them.

> ### Quick reference – Emissions displacement 
> 
> Occurs when emissions are successfully reduced from one source or in one area, but at the same time causes emissions to increase from another source or area.
>
> A good analogy is a train with some carriages being “green” and some being “dirty”. If you’re taking the train anyway, and move to a green carriage, you are not affecting the overall load of the train as a whole. Someone else will travel in the dirty carriage instead. The emissions from that train running are still exactly the same.
>
> <a href="https://en.wikipedia.org/wiki/Zero_Carbon_Displacement">Zero Carbon Displacement</a> requires strict analysis of an entire grid ecosystem to make sure that no additional fossil fuel based energy is being forced into use before it can be claimed.

In fact, your time-shifting may result in more than 100 tons of CO2 being generated for the day. That is because in the afternoon on this day, demand is also high. By deciding to shift your back up job to run at this time, you’ll add additional (unplanned) demand onto the grid. As a result of this, additional supply might need to be quickly ramped up to balance the grid. As we covered earlier, this extra supply is most likely going to come from a fossil fuel energy source.

Time shifting can also lead to grid instability because of these ever-shifting demand fluctuations.

So far, no actual gains to be made. You’ve not helped reduce carbon emissions. Operating as an individual, you probably haven’t impacted much by your time-shifting approach. However, things can become harmful if this is done at scale. But there are ways in which time-shifting can be refined to make it actually helpful, which we'll get to.

## 🌍 Applying the realities of grid management to compute location-shifting

> ### Quick reference – Location-shifting compute 
> 
> Looking for grids that have a greener fuel mix than your local one, and sending compute jobs to run on servers in that grid instead of your own.

To illustrate the idea, let’s imagine you are a fictional global corporation called Stoogle Tech. Every national branch needs to back-up its databases every day. Now imagine, each branch detects that the local grid in Lisbon is currently running on 80% renewables and 20% fossil fuels, and they all independently decide to send their backup jobs to run there.

Suddenly there is a whole lot of extra demand hitting Lisbon’s grid. The demand for the day will now no longer be the expected 100%, but say, 110%. 

The problem is that there is still only 80% of renewable energy available to Lisbon’s local grid. In order to keep electricity demand and supply balanced, Lisbon will most likely cover that extra 10% with fossil fuels. The international carbon-aware location-shifting initiative has just added extra emissions to Lisbon’s grid.

A **displacement effect** is seen again. These compute jobs have displaced the emissions from every other country to Portugal, for the same net emissions globally. Or has it?

In fact, it’s probably worse than that. Driving up demand in Lisbon and stimulating above-average fossil fuel consumption there has resulted in a net increase of CO2. Plus the electricity demand from each of the local regions didn’t actually reduce as a result of the jobs moving. The emissions in those local grids are still exactly the same. The global net consumption of electricity rose, as did CO2 emissions.

The implications become worse as things scale. Now imagine not just Stoogle Tech, but also Bircosoft Tech, Wapple Tech, and Macebook Tech all get on the location-shifting bandwagon. Let’s say all of their available servers are powered by national grids. Suddenly Lisbon’s electricity demand hits 120%, and local grid demand dips. 

Location shifting computing jobs makes no positive difference, just like time shifting. But it's adding emissions and potentially risking grid instability for others. In this regard, our well intentioned efforts are worse than those who just run their jobs when they feel like it, or better yet run them in a predictable fashion.

### How much location shifting would you need to trigger problems in practice?

Remember, upward and downward spikes can break grids, especially less resilient ones. It’s happened before in <a href="https://www.sciencedirect.com/science/article/abs/pii/S2214629621002607">Venezuela</a>, <a href="https://www.arabnews.com/node/1794836/middle-east">Iran</a>, <a href="https://www.reuters.com/article/us-georgia-tech-currency-analysis-trfn/analysis-crypto-tears-bitcoin-miners-face-blame-for-abkhazia-energy-crisis-idUSKBN2AT1UC">Georgia</a>, and <a href="https://www.cacianalyst.org/publications/analytical-articles/item/13709-did-cryptocurrency-miners-crash-the-central-asian-power-grid?.html">Kazakhstan</a>, among other places, when bitcoin mining created equivalent surges in computing-specific electricity demand.

Ultimately, the problems vary from grid-to-grid and depend on how resilient each grid is. To cause problems, you’d need a big spike in highly diversified grids, like Europe, or in grids that have invested heavily in storage, like California. But it could be quite modest to trigger serious impacts in less resilient grids like South Australia, with less grid interconnections and less fossil fuel energy for supply responses, or in India or South Africa, with less energy diversity.