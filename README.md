## PROMPT
Act as a Senior Game Developer who specializes in high-performance vanilla JavaScript, HTML5 Canvas, and algorithm optimization. 

Your task is to generate a fully functional, complete, and bug-free 2D Tower Defense game in a SINGLE HTML FILE. You must write the entire HTML structure, CSS styling, and JavaScript logic within this single file (inline CSS in <style> and inline JS in <script>). 

DO NOT use any external libraries, frameworks (like Phaser.js), or external image/audio assets. All visual elements must be rendered using HTML5 Canvas geometric primitives (fillRect, arc, etc.). 

Here are the strict technical specifications and game mechanics that you must implement:

1. ENVIRONMENT & UI:
- Canvas size: 800px width, 600px height.
- Create a sidebar/dashboard UI next to the canvas to display: Base Health (Start at 10), Coins (Start at 150), and Score.
- Do not use alert() for Game Over; draw a "GAME OVER" text directly on the canvas when health reaches 0 and stop the game loop.

2. PATH & BASE:
- Define a single, winding path using an array of specific coordinate waypoints (e.g., [{x:0, y:100}, {x:400, y:100}, {x:400, y:500}, {x:800, y:500}]).
- Draw the path with a distinct color (e.g., light gray).
- The enemy base/spawn point is at the start of the path, and the player's base is at the end.

3. ENEMIES:
- Spawn enemies periodically at the start of the path.
- Enemies must strictly follow the defined waypoints using vector movement calculations.
- Enemies are drawn as red circles.
- Each enemy has a health pool. If an enemy reaches the end of the path, deduct 1 from Base Health and remove the enemy from the array.
- If an enemy's health reaches 0, remove it from the array, add 20 Coins, and add to the Score.

4. TOWERS & PLACEMENT:
- The player can place a tower by clicking on the Canvas.
- Towers cost 50 Coins. Deduct coins upon successful placement.
- Towers are drawn as blue squares.
- Collision/Validation Constraint: Towers CANNOT be placed directly on the enemy path, and CANNOT overlap with existing towers.
- Each tower has a firing range (radius) and a specific fire rate (cooldown).

5. TARGETING & PROJECTILES:
- Each tower must iterate through the active enemies array, calculate the Euclidean distance, and find the nearest enemy within its firing range.
- When an enemy is in range and the cooldown is ready, the tower spawns a projectile (drawn as a small yellow circle).
- Projectiles must travel towards the target's current position using coordinate updating (not instant hit).
- Implement AABB or Circle-to-Circle collision detection. When a projectile hits an enemy, reduce enemy health and destroy the projectile.

6. ARCHITECTURE & OPTIMIZATION:
- Use `requestAnimationFrame` for the main game loop.
- Structure your code using JavaScript Classes/Objects (e.g., class GameManager, class Enemy, class Tower, class Projectile) for clean state management.
- Ensure strict cleanup of arrays (dead enemies and destroyed projectiles must be cleanly spliced to prevent memory leaks and redundant processing).
- Keep Cyclomatic Complexity as low as possible and avoid redundant loops.

OUTPUT REQUIREMENT:
Provide ONLY the raw, complete code block starting with `<!DOCTYPE html>` and ending with `</html>`. Do not provide partial code, placeholders like "// add logic here", or explanations. The code must be 100% ready to run in a browser.
