### Replace All Spaces

- [Question](#Question)
- [Though](#Though)

##### Question

Implement a function that replaces each space in the string with "%20".
For example:
	**Input**: "Sherlock Blaze is the most handsome boy in this world"
	**Output**: "Sherlock%20Blaze%20is%20the%20most%20handsome%20boy%20in%20this%20world"

##### Though

Directly, the problem is very simple, if we encounter a space, delete it, and insert "%20" in its place. Like this:

**Sherlock Blaze is the**
**SherlockBlaze is the**
**Sherlock%20Blaze is the**

If we create a pointer points to the start of this string. We can achieve the goal step by step as mentioned above.

But it's cost too much, O(n^2), because every time we delete or insert, we should move all the values after the space forward or backward.

**So, How to do better?**

What will happen if we don't have to move the elements backwards frequently?

In fact, we can calculate the length of the modified string in advance, then let a pointer point to it -- the end of our string growth, called J. The we let another pointer point to the end of the original string, called I.

The above string is too long, let us replace it with "a b c". So it's "a b c" now, we want "a%20b%20c".

First we calculate new length of the string. we got "a b c", its length is 6, we all know string in C saved like "a b c\0". The '\0' represents the end of the string. It looks like this.

![Origin String](../../pic/combat/replace_all_space/origin_string.png)

Now We need to replace space with "%20", so the new length of the string is 10.

![New String](../../pic/combat/replace_all_space/new_string.png)

Then we copy the value be pointed by I to the index pointed by J one by one.

![Step 1](../../pic/combat/replace_all_space/replace_step1.png)

![Step 2](../../pic/combat/replace_all_space/replace_step2.png)

Here is a little different when our pointer I encounters a space.

![Step 3](../../pic/combat/replace_all_space/replace_step3.png)
![Step 4](../../pic/combat/replace_all_space/replace_step4.png)

We Insert "%20" one by one in reverse order.

![Step 5](../../pic/combat/replace_all_space/replace_step5.png)

When it finished, pointer I move forward for next value.

![Step 6](../../pic/combat/replace_all_space/replace_step6.png)

![Step 7](../../pic/combat/replace_all_space/replace_step7.png)

And findlly we achieve our goal.