## Modelling Moths and Beetles with the Iterated Prisoner’s Dilemma

## The Prisoner's Dilemma

>Two men are caught on suspicion of committing a crime and taken to the police
>station. The police officers are sure that these two have committed the crime however, they
>do not have enough evidence to charge them of major crimes. If neither two confesses to
>the crime, they would simply be charged on petty conditions and jailed for one year. But,
>if one of them confesses and the other does not, then the confessor would spend no time in
>jail whereas the other, would be jailed for three years. If both of them confess, then they will
>each be jailed for two years. The pair have no way of meeting or communicating with each
>other. What is the best strategy?

The table below shows the **Payoff Matrix** from our Prisoner’s Dilemma game for the two players.

|           |Defect|   | Coop |   |
| --------- |:----:|:-:| ----:|:-:|
| Defect    |      | 2 |      | 1 |
|           | 2    |   | 4    |   |
| Cooperate |      | 4 |      | 3 |
|           | 1    |   | 3    |   |

## Moths vs Beetles

The model we have set up bears a slight resemblance to standard Predator-Prey Population
models. Instead, there are two species attempting to form a harmonious cohabitation.
Our first specie is the moth. Or the Crambidae to be more precise, who are commonly
known as the grass moth family. Our second specie is from the Phyllophaga genus of beetles.
These two were chosen as they eat similarly and share similar habitats. Thus we wanted to
examine whether they could live side by side.
Our environment is a closed, bounded lawn. For if it were not closed and bounded then
the one specie can simply fly away and that would defeat the point. Our lawn starts off
filled with grass and with plenty of foliage. The cohabitants move across the lawn randomly,
taking a step at a time, eating very small amounts of the grass. However, when a cohabitant
bumps into another on the same patch of grass, encouraged to eat more, they have to decide
what share each of them gets. This is where the Prisoner’s Dilemma comes in.

 Here it implies the amount of grass the cohabitant would get depending on whether they decided to Cooperate
 or defect. With (D, D) being the only point of Nash Equilibria (i.e. if they
both defect), it might seem like the best option but not necessarily the most altruistic one.
But the cohabitants get given a strategy that they must stick to. Depending on whether they
have decided to defect or cooperate and on the decision of their opponent, the cohabitant
grass gain will lead to points using the payoff matrix.

The cohabitants will continue to live and interact until one of the following occurs:
* The grass runs out thus there is no more food left. This leads to a loss for the user.
* The maximum personal score of the cohabitants reaches 250. This becomes a win
for the user as the cohabitants have managed to interact well but still live together
without running out of the grass.
* And finally, if the ticks reach 5,000. This again indicated a win.

## Strategies

### Tit-for-Tat

Tit-for-Tat starts off cooperating and then simply copies the opponents previous decision for the rest of
the game. This can be seen as quite a nice method as the player using it, is never tempted
to defect itself unless the other opponent defects. And even if it does defect, it is quick to
forgive if the opponent decides to go back to cooperating.

### Random

This implies that the player (i.e. the moth or beetle) will randomly choose between defecting and cooperating each time.

### Always Defect / Always Cooperate

If this is chosen, the player will always defect (or cooperate) on every turn.

### Altruistic Strategies

It is natural for species to want to work together to provide their family with a better
outcome. Certain insects, commonly show high levels of altruism when it comes to different
aspects of life. Here, each cohabitant, would want their specie to thrive. For this reason, we
added an altruism switch for each breed. This switch, when turned on, allows the cohabitant
to use whichever strategy it was given however, if it faced with an opponent from the same
family (i.e. same breed), it will always cooperate with them. This additional feature only
affects the Random strategy and the Always Defect strategy.

## How It Works

The colour of our lawn starts off at a bright green. We’ll now recall that as the moths and beetles move across the patches, the
patch loses some colour as a bit of grass has been eaten. Then the colour loses its green by
a ceratin amount. This happens every time a moth or beetle moves across the given patch. To stick to
the grassland aesthetic, we avoid having black and white patches by skipping certain shades
when the colour is decreasing. The lowest colour a patch can be is bright brown. This
resembles the soil and indicates grass shortage.

When the cohabitants interact with one another, since there is then a greater amount of
grass eaten, the patch loses colour by five times the amount that it would lose if there was only one cohabitant on it. Notice that here the colour loss is five times greater
than before. This number was chosen as the the maximum total payoff in the Prisoner’s
Dilemma is 6 whist the lowest is 4. Once a patch’ colour reaches that bright brown, no more interactions
can take place on it as there is no longer any grass thus no need for an interaction.

### Tit-for-Tat Method

To use Tit-for-Tat, the cohabitants need to remember all the opponents it has faced and the
last decision of this partner. To do this, each moth and beetle is set an empty list at the
start. This list then gets filled with all the partners it faces. Then after every interaction
a *directed link* is created from the cohabitant to its partner. The link is then given a
variable *decision* where the last decision of the cohabitant will be saved. Then when the
cohabitant meets its partner again, they will recall the link and the *decision* variable to
incorporate it. The variable is updated after each interaction with the partner.

## Evolutionary Tournament

In our model, there is also the option to host an evolutionary tournament. An evolutionary
tournament consists of different rounds. After each round, a new generation of moths and
beetles are born. The number of moths being born in the next round depends is a third of
the average personal score of the moths in the round just ended. Similarly, for the beetles.
The round ends when the maximum personal score of the cohabitants surpasses 160. This
can be obtained from a minimum of 40 interactions and a maximum of 160 interactions.
Due to the fact that the cohabitants move randomly and that they can only interact on
non *soil-only* patches, interactions didn’t always happen as often as one would think. Thus
after on running some tests and seeing how quickly the maximum personal score rises, we
concluded that 160 was the best figure to indicate the end of a round.

## Small-Scale Evolution

In addition to the evolutionary tournament, we wanted to look at how the species would
evolve by introducing a new generation without eliminating the older generation. To do
this, we added the swtich *Offspring*. When this switch is enabled, any moth or beetle who
has reached a personal score of 100, is allowed to reproduce. Each cohabitant is limited to
one child only to avoid creating swarms in the model. Additionally, any cohabitant that
reached a certain age (1500 ticks) that had a low personal score (50), would then go on to
die. This was intriguing way of modelling evolution without creating rounds and hosting
a long tournament. It also made our model in-tune with what actually happens in large
colonies of moths and beetles

## Stag Hunt

In addition to the Prisoner’s Dilemma, there is the option to model the Moths and Beetles
with an iterated version of a different game: Stag Hunt.

>A pair go to hunt. They must decide whether to hunt a hare or a
>stag. A stag is worth more than a hare but a stag can only be hunted successfully if both>
cooperate. Each player must decide which to hunt without knowing their partner’s decision.

|           |Defect|   | Coop |   |
| --------- |:----:|:-:| ----:|:-:|
| Defect    |      | 2 |      | 1 |
|           | 2    |   | 3    |   |
| Cooperate |      | 3 |      | 4 |
|           | 1    |   | 4    |   |

We now have two **pure strategy Nash equilibria** (D, D) and (C, C).
