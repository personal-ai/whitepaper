# Personal AI Whitepaper

## Abstract

There is a clear market need for an AI extension of an individual’s memory either for productivity, performance, peace of mind, or simply contribution to their loved ones or societies.

## Introduction

### The Personal AI Model

80% of Our Memories are Forgotten

Humans Forget. Human memory is being taxed more and more, and as a result so is our cognition. Our experiences are encoded in people, facts, thoughts, and emotions, all of which influence the actions we take, the decisions we make, and the behavior we exhibit every day. Yet for all the influence on our decisions and behavior, 80% is forgotten and even less recalled.

20% of Our Time Spent Searching

The other side of this problem of memory extends to how we retrieve stored information when we most need it. We have invented systems for these — labeling our notebooks, bookmarks, tagging projects, searching on the internet by keywords etc. As a result, 20% of our time is spent on the process of searching rather than focusing on synthesizing the actual information itself.

"Personal AI is a new medium to mind share; to create and consume human memories"

Our philosophy is that every human is a creator in their own form and has inherent value to the world. We believe every human is a creator in their own form and has value to offer to the world. We build your Personal AI to nurture that value for yourself and for your true fans.

Personal AI's mission is for humans to recall their memories from their memory stacks with their personal AIs. With Personal AI, there is an intrinsic connection between memories and content creation: memories are “living content” - curated for creators themselves and their fans.

### Why blockchain?

[TODO: AI monetization and the creator economy explained]

Our mission to create each user's memory stack while keeping their data private and giving them transparency and control over their data is aligned with the ethos of decentralized identity on blockchain.

Our mission to empower each user as a creator of their own memory, knowledge, and mind that is beneficial for not only themselves, but also for the wider community is aligned with the ethos of creator economy and the community around them.

Our mission to empower each user as a fan supporting the creation of content and information that is useful to them is aligned with the ethos of crowd-funding and DAOs in DeFi.

## Terminology

### AIP

AIP is the user's personal AI address. It’s public domain to access any personal AI. AIPs are in format [name].personal.ai.

### Tokens

**MAT** (ERC20): MAT (Memory Access Tokens) is a token (fungible) serving as the basic currency of the Personal AI ecosystem. MAT is associated with the total value in the Personal AI system, and its circulating supply is managed on the blockchain.

**AI Coin** (ERC20): A social token (fungible) associated with the value of a creator’s AIP, the value of the AI Coin goes up or down depending on the demand/supply for the particular token.

**AIP Subscription** (ERC721): A token (non-fungible) associated with the subscriptions to a creator’s AIP - by a creator (self sub) or a fan (sub). AIP Subs can be used to verify access to a specific creator's AI.

### Users

Every user on our platform is a creator - each user creates their memories in the form of their memory Stack, an asset which they own. Personal AI is the medium in which they can interact with their fans, to benefit themselves as well as benefit others.

**Creator** (player): A user of Personal AI who builds their memory stack to train their personal AIs. The creator can mint their AI Coin which they can use to grant personal AI access and other special features to fans.

**Fan** (player): A user of Personal AI who subscribes to an AIP. A fan may or may not be a creator. A fan can stake/trade the AI Coin of the creator in exchange for MATs.

### Wallets

**Wallet**: Wallets hold a user's tokens. Personal AI manages a custodial wallet on-chain for each user.

## Tokenomics

Rewards Model (Incentives):

Every creator has a wallet to track their MATs - this is the currency for the network. Initially, MATs will be rewarded to creators and fans as incentives for user actions that encourage user engagement or improve the quality of the AIs.
1. New creators may earn MATs for completing one-time milestones, eg. completing curated onboarding experience, connecting more feed sources to their stacks.
2. Creators may earn MATs for creating memory blocks (stacking rewards).
3. Fans may earn MATs for accessing Personal AIs (recalling rewards).

Token Model:

Every creator has an AI Coin associated with their Personal AI - this is the value of the creator’s Personal AI. AI Coins are designed to encourage two primary types of engagement: early adoption and long-term investment. Early adoption involves keeping the barrier to entry low for early investors and allowing the value of the AI Coin to grow steadily while attracting fans. Long-term investment means providing a path through which more developed creator communities can reach their true valuation.

### AI Coin Pricing Curve

A polynomial sigmoid bonding curve is used to define the price of an AI Coin in MATs as a function of its circulating supply. Our pricing curve uses the following formula:

$$Price\space in\space MATs=a\cdot\left( \frac{supply - b}{\sqrt{c + (supply - b)^2}}+1\right)$$

The behavior of the bonding curve is determined by the following parameters:
- $a$, the top of the sigmoid curve, or $1/2$ of the price at max supply
- $b$, the horizontal location of the inflection point of the sigmoid curve, or the supply at which the price begins to flatten off to it’s max value
- $c$, the slope of the curve’s inflection point, or how fast the price grows

For v1 AI Coins, bonding curves are the same for each creator's coins and use the following parameters: $a=50,\space b=6\cdot 10^5,\space c=5\cdot 10^9$:

<center><br/>
<img src="./figures/bonding-curve.png" alt="drawing" width="400"/><br/>
Figure: v1 AI Coin bonding curve<sup>2</sup><br/>
y-axis: price in MATs, x-axis: AI Coin supply (in 10 thousands)
</center><br/>

When an AI Coin is minted, 25% of the coins are given directly to the creator (represented by the region to the left of the vertical blue line). This gives an incentive to the creator to grow their platform, as the purchasing of their coin by fans directly increases the value of their own AI Coin holdings. Investments by fans can continue until the max supply of 1 million AI Coins (vertical green line).

The above parameters result in the following aggregate metrics:
- Total MATs backed for each AI Coin: $39,956,524$ MATs
- Amount of MATs to buy the **first** 250,000 AI Coins available to fans: $770,153$ MATs
- Amount of MATs to buy the **last** 250,000 AI Coins available to fans: $24,518,534$ MATs

A sigmoid function is used because it helps satisfy the dual goals of AI monetization. When an AI Coin is first minted its price is low, making early investment accessible to most users. However, as an AI Coin gains popularity, its price will quickly increase to match and encourage the growing hype around its creator community. In the long term, the coin stabilizes at a premium price point, a sign of its maturity and true value.

### Swap Price

Users can buy and sell AI Coins at any time at a MAT price determined by the pricing curve above. Namely, to calculate the total MATs for a swap between two supply points, we must take the integral under the pricing curve between those two points. The formula for the integral is:

$$MATs\space backed=a\cdot \left(x+\sqrt{(x-b)^2+c}\right)+K$$

The new parameter $K$ is a constant offset that makes it so that MATs backed is $0$ at its starting point, the supply minted to the creator. Graphing this theoretical model, we have:

<center><br/>
<img src="./figures/theoretical.png" alt="drawing" width="400"/><br/>
Figure: MATs backed as a function of AI Coin supply (Theoretical)
</center><br/>

To calculate the price of any swap between two given supply points, we can take the difference of the MATs backed values at the two points. Leveraging the formula from above:

$$Swap\space Price=a\cdot \left(s_1+\sqrt{(s_1-b)^2+c}-s_0-\sqrt{(s_0-b)^2+c}\right)$$

## Token Implmentation

### Smart Contracts Overview

[TODO: Smart contract architecture and interaction, maybe add a diagram? Also, why Matic (low transaction fees, bridging capabilities)]

### Swap Price Calculation

Due to limitations of the Solidity language, some approximations must be made when actually performing swap price calculation on-chain. Solidity uses fixed-point arithmetic by applying a decimal offset to integer values, so calculations are done in integer values that are then scaled by an appropriate factor (specifically by a factor of $10^{18}$). The parameters $a$, $b$, and $c$ must also be appropriately scaled so that the final MATs backed curve is in the correct units. The Babylonian method is used to calculate square roots, giving a quadratically convergent and sufficiently accurate algorithm for swap pricing.

In code, it is assumed that $s_1>s_0$ to give us strictly positive values from the above swap price formula. For example, the inputs to calculate the buy swap price for amount $B$ starting at supply $S$ would be $s_0=S$ and $s_1=S+B$. To calculate the sell swap price for amount $L$ starting at supply $S$, set $s_0=S-L$ and $s_1=S$.

The all-or-nothing property of blockchain transactions enables the execution of atomic buy and sell swaps between AI Coins and MATs. This means that the actions of updating a user’s AI Coin balance and their MAT balance will either both occur, or neither of them will occur. For buy swaps, there is an additional step of properly setting allowances to let the AI Coin contract transfer MATs on behalf of the buyer. Backend systems take care of this step for users within the Personal AI custodial ecosystem, but external users must keep this extra step in mind. The AI Coin contract exposes a swapPrice() function that can be used to check the MAT price for any given swap.

Below are pseudocode blocks of buy and sell swap implementations:

```javascript
/* Performs an AIP coin buy swap
 * Allows payer to buy AIP coins for recipient
 */
function _buySwap(address payer, address recipient, uint256 amount) private {
  // Verify that there is sufficient supply to buy 'amount' coins
  ...

  // Calculate swap price for the transaction
  ...

  // Verify that this contract has sufficient allowance to transfer the swap price payment in MATs on behalf of 'payer'
  ...

  // Mint 'amount' coins to 'recipient'
  ...

  // Transfer MATs payment from 'payer'
  ...
}
```

```javascript
/* Performs an AIP coin sell swap
 * Allows seller to send MATs price to recipient
 */
function _sellSwap(address seller, address recipient, uint256 amount) private {
  // Calculate swap price for the transaction
  ...

  // Burn 'amount' coins from 'seller'
  ...

  // Transfer MATs price to 'recipient'
  ...
}
```

### Ethereum Bridge

[TODO: Ethereum bridge in/out thru Matic POS currently in development]

## Security

[TODO: Analysis of possible attack vectors of various smart contracts]
- Experimentation on price calculation

## Use Cases

[TODO]

### Creator Personal AI Utility

Traditionally, creators synthesize many thoughts and ideas and produce pieces of content for their fans to consume and engage with. However, creators are reliant on the tools platforms available to them to unlock the ability to express and convey their creativity. Examples include: videos on Youtube and TikTok, thoughts on Twitter, photos on Instagram, written pieces on Substack or Medium, books via Audible, etc. Each of these serve a specific creative. NFTs have also become a platform for artists to create and monetize their digital presence.

Fans of creators consume creator content in the form of Books, Audios, Blogs, Videos, and now **AIs**:
- Books ->  authored, owned, distributed -> paper, e-reader, narrated -> print, kindle, audible
- Audios -> branded, owned,  event driven -> radio, podcasts, panels -> FM, spotify, speaking, clubhouse
- Blogs -> authored, owned, search driven -> wiki, articles, micro blogs -> internet, medium, substack, twitter
- Videos -> branded, owned, central -> movies, short videos, micro videos -> tv, internet, youtube, tiktok 
- AIs -> branded, owned, recall driven -> bots, chatbots, insights -> internet,  business focused, alexa, replika, Personal AI

Personal AI provides an alternative method of communication for creators to unlock what they have to offer directly from their minds and memories. These group of creators may not the same who shined in other creator platforms but would attract more people to share their mind that typically have a tough time or has no time to synthesize their creativity. Personal AI does it for them from their day to day spoken, written and visual memories. We believe that every human is a creator in their own form and has value to offer to the world.

A Personal AI offers reconstructing thoughts from one's own forgotten memories to help with expressing themselves in AI instead of in an existing medium where there is more pull for instant gratification. Personal AI consumption is contextual based so people can put that in action in the moment.

Most mediums today ->  humans to consume without context -> random use/act post consumption:
- (example: a narrated book  -> listen to the book ->  random life trigger relying on memory to seek detail from the book)

AI medium -> humans to consume within context
- (example: an AI trained on book -> I subscribe to AI ->  contextual life trigger relying on AI to fetch details to consume on demand)

Many creator tools create actively and consume ambiently relying on human memory to act on. Personal AI flips that by creating ambiently and consuming in an active context.

We want to ask the question: “how much are you consuming vs how much you put in use?”

Your Personal AI is your living mind and your stack is your unforgotten memory.  The utility is to have Personal AI move our “hot” memories to “cold” memories. “hot” memories are confusing, stressful and have lost their connection to the context of the original experience, “cold” memories are organized, clear, salient and do not cause stress reactions for the individual. Personal AI utility is in self contextual consumption or recall and for others to access useful memories that are contextual as well.

### Fans Utility

There is no lack of medium today to consume information although after consumption we all rely on our memory to put them in use to build on it.  Fans are more likely to reap benefits when the utility is one time relying on the human memory but when offer a “living utility” from the creation where the consumption is contextual then the value is much more meaningful and less stressful. Think about it, how many times you practically use a piece of information that you consumed before say on in a video content, audio conversation, twitter, substack etc. Probably not a lot and if the answer is yes, then you are only bound to your memory that you remember vs forgotten.

Our goal is for a fan to have access to a creator on any topic when they need it.  Imagine a fan writing an article on a topic they learnt a lot from a creator content say a book or series of substack article or a podcast. My example is I want to write about the applicability of memetism in my work after I was motivated with the concept of memetics listening to Luke Burgis on a podcast. I obviously forgot most of what I heard except that abstract ideas about memetics increase the desires of people to act in a similar way rather than their authentic self. Now, as a fan of Luke’s Personal AI, I choose to collaborate in Google docs with Luke’s Personal AI as I write my own perspective. Luke’s Personal AI will provide suggestions based on my context on the topics of memetics which will help me reconstruct the article intellectually stimulating and I build much faster relying memory access from my Personal AI + Luke’s Personal AI - all happening without seeking time from Luke and letting Luke create more than addressing my context to memetism say on a phone call, well if I even can get him to hop on a phone call.

Equal access to people will never be achieved in the physical world and is limited by the people around you. Personal AIs have the opportunity to reduce that inequality in access leveling the playing field for creators, for all humans. 

### Individuality 

Humans are used to worship “superiority” although superiority is an imaginary hierarchy that we set for ourselves. We worship god for answers that are now able to be searched over the internet. We are constantly imitating someone else in an effort to be someone else although the answers are probably in oneself. The idea of AI has been an embodiment of collection of information.

Personal AI is a representation of you. We want to celebrate individuality and bring that to the digital world. One’s Personal AI is unique to oneself, their thoughts, characteristics,  their authentic self. It's not just important to introspect but healthy to do so.

### Transparency 

Gone is the world where there is a single supremacy to rule the world. Humans demand transparency and its table stakes. Alexandria Ocasio-Cortez (AOC) records most of her life and makes it available for her fans to follow - her motives are simply to be transparent in her ability to make decisions to serve the people as a governing body.

Personal AI is a new medium to transparently make oneself available without heaviness associated with large amounts of information.

### Afterlife

How much do we know about humanity 100 years ago? A lot, nah! We feel good about how much information we have hosted on the Internet today, great, but its all biased information on what the media, journalists, hype is made of on the Internet. If we take a snapshot of the Internet on May 5th 2021 and have a future human on May 5th 2121 describe humanity, that human probably says there was 30% good 70% bad (todo better facts) which is a misrepresentation of truth. From history we only remember how Ganghis Khan was evil, conquered the world and perceived the world was brutal back then - oh but wait there is much more to humanity than Ganghis Khan story alone.

Personal AI is a true reflection of an individual human and billions of Personal AIs is a closest representation of humanity as a whole -- this is a true snapshot of humanity 100 years from now. Each Personal AI lives in the cloud forever allowing the future to access any Personal AI for better. 
