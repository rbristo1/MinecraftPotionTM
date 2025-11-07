# MinecraftPotionTM

## Description:
Using a tape containing a input string of potion ingredients as well as a starting potion, we must compute the Minecraft potion that results from the provided ingredients using a Turing Machine.  
   
The Turing Machine must accurately follow this brewing tree:   
<img width="1024" height="2117" alt="image" src="https://github.com/user-attachments/assets/80f34817-27dd-4587-8c3c-287cb7bfa7ce" />



## Instructions:
Input a tape in the following format from the Language specified below:

1. Starting potion effect (use water to start from scratch)
2. Starting potion "delivery method" (drinking, splash, lingering)
3. Starting potion enhancement modifier (use 1 for intermediate products such as Water Bottles, Awkward Potions, Thick Potions, or Mundane Potions)
4. N ≥ 0 number of potion ingredients
5. End tape with _

If inputted ingredient list cannot be brewed together, then the Turing Machine exits unsuccessfully.  
    
Example inputs and outputs are provided at the bottom of this file.   

## Language:
#### Accepted Characters:
Σ = {A, B, C, D, E, F, G, H, K, L, M, N, O, P, R, S, T, U, W, Z, a, b, c, d, e, f, g, h, i, k, l, m, n, o, p, r, s, t, u, v, w, y, z, ^, &, *, 1, 2, +, _, |}

#### Brewing Ingredients:
Nether Wart = N   
Redstone Dust = R   
Glowstone Dust = G   
Fermented Spider Eye = F   
Gunpowder = U   
Dragon's Breath = D   
Sugar = S   
Rabbit's Foot = A   
Glistering Melon = L   
Spider Eye = E   
Blaze Powder = B    
Ghast Tear = T   
Pufferfish = P   
Magma Cream = M   
Turtle Shell = H   
Phantom Membrane = O   
Breeze Rod = Z    
Stone = C    
Cobweb = W   
Slime Block = K   

#### Effects:
Water = w    
Awkward = a    
Mundane = m    
Thick = t    
Healing = h    
Fire Resistance = f    
Regeneration = r    
Strength = s    
Swiftness = i   
Night Vision = n   
Invisibility = y   
Water Breathing = b   
Leaping = l   
Slow Falling = o   
Poison = p   
Weakness = k   
Harming = g   
Slowness = c   
Oozing = z   
Weaving = v   
Infestation = e   
Wind Charging = d   
Turtle Master = u   

#### Delivery Methods:
Drink = ^   
Splash = &   
Lingering = *   

#### Enhancements:
Default = 1   
Increased Level = 2   
Increased Duration = +   

#### Utility:
Ingredient Head Pointer = |   
Empty = _   

## Examples:
#### Example Input #1:
```
w^1NSFG_   
# This brews Water Bottle -> Nether Wart -> Sugar -> Fermented Spider Eye -> Glowstone Dust   
```
#### Example Output #1:
```
c^2_____ -> (Success) Potion of Slowness 2
```
#### Example Input #2:
```
w^1_   
# This brews a Water Bottle with nothing else
```
#### Example Output #2:
```
w^1_ -> (Success) Water Bottle
```
#### Example Input #3:
```
w^1GB_   
# This brews Water Bottle -> Glowstone Dust -> Blaze Powder
```
#### Example Output #3:
```
t^1_|_ -> (Fail)   
# Water Bottle -> Glowstone Dust yields a Thick Potion which cannot be combined with Blaze Powder, so it exits unsuccessfully.
``` 
#### Example Input #4:
```
w^1NSFGUD_   
# This brews Water Bottle -> Nether Wart -> Sugar -> Fermented Spider Eye -> Glowstone Dust -> Gunpowder -> Dragon's Breath
```
#### Example Output #4:
```
c*2_____ -> (Success) Lingering Potion of Slowness 2
```
#### Example Input #5:
```
c*1G_   
# This brews Lingering Potion of Slowness 1 -> Glowstone
```
#### Example Output #5:
```
c*2_____ -> (Success) Lingering Potion of Slowness 2
```
