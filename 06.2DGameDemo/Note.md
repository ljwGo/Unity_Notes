```c#
void Update()
{
  float h = Input.GetAxisRaw("Horizontal");
  moveDistance = h * moveSpeed * Time.deltaTime;
}

private void FixedUpdate() {
  character.Move(moveDistance, false, false);
}
```



```c#
void Update()
{
  h = Input.GetAxisRaw("Horizontal");
  if (!isJump) {
    isJump = Input.GetButtonDown("Jump");
  }
}
private void FixedUpdate() {
  float moveDistance = h * runSpeed * Time.fixedDeltaTime;
  character.Move(moveDistance, false, isJump);

  isJump = false;
}
```



在Project Settings下的InputManager添加新的按键类型, 将Type改为Key or Mouse Button



```c#
public void OnLand() {
  anim.SetBool("IsJump", false);
}
```



```c#
if (canJump && jump)
{
  // Add a vertical force to the player.
  //Debug.Log("In Add Force: " + Time.time);
  canJump = false;
  m_Rigidbody2D.AddForce(new Vector2(0f, m_JumpForce), ForceMode2D.Impulse);
}
```

