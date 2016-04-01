# GameUnity-BinaryDude-
First game in Unity
//level manager


 public GameObject deathParticle;
    public GameObject respawnParticle;

    public float respawnDelay;

    // Use this for initialization
    void Start () {

        player = FindObjectOfType<PlayerController>();
	
	}
	
	// Update is called once per frame
	void Update () {
	
	}

    public void RespawnPlayer()
    {
        StartCoroutine("RespawnPlayerCo");
    }

    public IEnumerator RespawnPlayerCo()
    {
        Instantiate(deathParticle, player.transform.position, player.transform.rotation);
        Debug.Log("Player Respawn");
        yield return new WaitForSeconds(respawnDelay);
        player.transform.position = currentCheckpoint.transform.position;
        Instantiate(respawnParticle, currentCheckpoint.transform.position, currentCheckpoint.transform.rotation);
    }
}
