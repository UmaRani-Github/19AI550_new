# Ex.No: 10  Implementation of 2D/3D Game Development Using Unity
### DATE: 04/09/2026                                                                         
### REGISTER NUMBER : 212225230204


### AIM: 
To design and develop a simple 3D Coin Collector game using Unity, where the player moves using keyboard controls, collects coins, maintains a score, and displays a YOU WIN! message after collecting all coins.


### Algorithm:
```
1. Start Unity and create a 3D game project.
2.Create a ground using a Plane.
3.Create a Player using a Capsule.
4.Add Rigidbody and Collider components to the Player.
5.Create a C# script to control Player movement using W, A, S, D keys.
6.Create five coin objects using Cylinders.
7.Add a C# script to rotate and collect the coins.
8.Set the coin colliders as Triggers.
9.Create a Canvas and add a score text displaying Coins: 0.
10.Create a GameManager to update the score whenever a coin is collected.
11.Display YOU WIN! when all five coins are collected.
12.Test the game in Unity.
13.Save the Unity project.
14.Upload the project to the required GitHub repository.
```  
### Program:
1.PlayerMovement.cs
 ```
using UnityEngine;

public class PlayerMovement : MonoBehaviour
{
    public float speed = 5f;

    void Update()
    {
        float horizontal = Input.GetAxis("Horizontal");
        float vertical = Input.GetAxis("Vertical");

        Vector3 movement = new Vector3(horizontal, 0f, vertical);

        transform.Translate(movement * speed * Time.deltaTime);
    }
}
```


2.Coin.cs
```
using UnityEngine;

public class Coin : MonoBehaviour
{
    void Update()
    {
        transform.Rotate(0, 100 * Time.deltaTime, 0);
    }

    private void OnTriggerEnter(Collider other)
    {
        if (other.CompareTag("Player"))
        {
            GameManager.instance.CollectCoin();
            Destroy(gameObject);
        }
    }
}
```


3.GameManager.cs
```
using UnityEngine;
using TMPro;

public class GameManager : MonoBehaviour
{
    public static GameManager instance;

    public TextMeshProUGUI scoreText;
    public TextMeshProUGUI winText;

    private int score = 0;

    void Awake()
    {
        instance = this;
    }

    void Start()
    {
        scoreText.text = "Coins: 0";
        winText.text = "";
    }

    public void CollectCoin()
    {
        score++;
        scoreText.text = "Coins: " + score;

        if (score >= 5)
        {
            winText.text = "YOU WIN!";
        }
    }
}
```
### Output:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/93c76d86-7feb-491d-acb1-410d313d50ba" />

### Result:
Thus, a simple 3D Coin Collector game was successfully designed and developed using Unity. The Player movement, coin collection, score counter, winning condition, and colorful game environment were successfully implemented and tested.
