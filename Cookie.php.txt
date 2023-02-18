<?php
if (isset($_COOKIE['color'])) {
    $color = $_COOKIE['color'];
    $expire_time = $_COOKIE['expire_time'];

    // If the cookie has expired, delete it
    if ($expire_time < time()) {
        setcookie('color', '', time() - 3600);
        setcookie('expire_time', '', time() - 3600);
        $color = 'white';
    }
} else {
    $color = 'white';
}
?>

<!DOCTYPE html>
<html>
<head>
    <title>Cookie Example</title>
</head>
<body style="background-color: <?php echo $color; ?>;">
	<h1> Cookie Example</h1>
	<p>Time zone: Asia/Dhaka</p>
	<hr>
    <br>
    <h3>Set Cookie</h3>
    <br>
	<hr>

    <form method="POST" action="set_cookie.php">
        <label for="color">Select a color:</label>
        <input type="color" name="color" id="color" value="<?php echo $color; ?>">

        <br><br>

        <label for="expire_time">Expire on:</label>
        <input type="datetime-local" name="expire_time" id="expire_time" value="<?php echo date('Y-m-d\TH:i', time()); ?>">

        <br><br>

        <button type="submit">Set Cookie</button>
    </form>

    <hr>
    <br>
    <h3>Destroy Cookie</h3>
    <br>
    <hr>

    <form method="POST" action="destroy_cookie.php">
        <button type="submit" name="destroy" value="true">Destroy Cookie</button>
    </form>
</body>
</html>
