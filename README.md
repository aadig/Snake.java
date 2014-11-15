Snake.java
==========
package ArrayFun;

import zen.core.Zen;

public class Snake {

	int x = 250;
	int y = 250;
	int dx = 10;
	int dy = 0;
	Snake next = null;

	public void draw() {
		Zen.setColor("blue");
		Zen.fillRect(x, y, 10, 10);
		if (next != null) {
			next.draw();
		}
	}

	public void die() {
		x = 250;
		y = 250;
		next = null;
	}

	public boolean dead() {

		Snake current = next;
		while(current != null) {
			if (current.x == x && current.y == y) {
				return true;
			}
		}
		return false;
	}

	public void move() {

		x = x + dx;
		y = y + dy;
		if (next != null) {
			next.move();

		}
	}

	public void checkKeys() {
		if (Zen.isKeyPressed("up") && dy != 10) {
			dx = 0;
			dy = -10;
		}

		if (Zen.isKeyPressed("down") && dy != -10) {
			dx = 0;
			dy = 10;

		}

		if (Zen.isKeyPressed("left")){
			dx = -10;
			dy = 0;
		}

		if (Zen.isKeyPressed("right")) {
			dx = 10;
			dy = 0;
		}
	}

	public void grow() {
		if(next == null) {
			next = new Snake();
			next.x = x - dx;
			next.y = y - dy;
			next.dx = dx;
			next.dy = dy;

		}

		else {
			next.grow();
		}
	}

}
