#210222~210226

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
<link rel="stylesheet" href="Style.css">
<script src="https://code.jquery.com/jquery-3.4.1.js"></script>
<script>
	var articles = [ 'article1', 'article2', 'article3', 'article4',
			'article5', 'article6' ];
	$.article_select = function(article) {
		$.each(articles, function(index, el) {
			$('#' + el).css('display', 'none');
		});
		$('#' + article).css('display', 'block');
	}

	$(function() {
		$.article_select(articles[0]);
		$('.btn').click(function() {
			$.article_select(articles[Number($(this).attr('id')) - 1])
		});

		$('input[type=radio]').change(function() {
			if ($(this).val() == 'normal') {
				$('select').attr('disabled', 'disabled');
			} else {
				$('select').removeAttr('disabled');
			}
		});

		$('#login').submit(function(event) {
			if ($('#login_id').val().length == 0) {
				alert('아이디를 입력하세요.');
				event.preventDefault();
				$('#login_id').focus();
				return;
			}
			if ($('#login_pass').val().length == 0) {
				alert('비밀번호를 입력하세요.');
				$('#login_pass').focus();
				event.preventDefault();
			}
		});

		$('#make_acc').submit(function(event) {
			if ($('#make_id').val().length == 0) {
				alert('계좌번호를 입력하세요.');
				event.preventDefault();
				$('#make_id').focus();
				return;
			}
			if ($('#make_name').val().length == 0) {
				alert('이름를 입력하세요.');
				$('#make_name').focus();
				event.preventDefault();
				return;
			}
			if ($('#make_money').val().length == 0) {
				alert('입금액를 입력하세요.');
				$('#make_money').focus();
				event.preventDefault();
			}
		});
		
		$('#deposit').submit(function(event) {
			if ($('#deposit_id').val().length == 0) {
				alert('계좌번호를 입력하세요.');
				event.preventDefault();
				$('#deposit_id').focus();
				return;
			}
			if ($('#deposit_money').val().length == 0) {
				alert('금액을 입력하세요.');
				$('#deposit_money').focus();
				event.preventDefault();
			}
		});
		
		$('#withdraw').submit(function(event) {
			if ($('#withdraw_id').val().length == 0) {
				alert('계좌번호를 입력하세요.');
				event.preventDefault();
				$('#withdraw_id').focus();
				return;
			}
			if ($('#withdraw_money').val().length == 0) {
				alert('금액을 입력하세요.');
				$('#withdraw_money').focus();
				event.preventDefault();
			}
		});
		
		$('#acc_info').submit(function(event) {

		});
		
		$('#all_acc_info').submit(function(event) {

		});

	})
</script>


</head>
<body>
	<div class="container">
		<header>
			<h1>멀캠은행</h1>
		</header>
	</div>

	<div class="container">
		<nav>
			<ul class="account">
				<li><a href="#" id='2' class='btn'>계좌개설</a></li>
				<li><a href="#" id='3' class='btn'>입금</a></li>
				<li><a href="#" id='4' class='btn'>출금</a></li>
				<li><a href="#" id='5' class='btn'>계좌조회</a></li>
				<li><a href="#" id='6' class='btn'>전체계좌조회</a></li>
			</ul>
			<ul class="login">
				<li><a href="#" id='1' class='btn'>로그인</a>
			</ul>
		</nav>
	</div>


	<div class="container">
		<section id="main">
			<article id="article1">
				<form action="#" method="post" id="login">
					<h2>[ 로그인 ]</h2>
					<br>
					<table>
						<tr>
							<td>아이디</td>
							<td><input type="text" name="id" id="login_id" /></td>
						</tr>
						<tr>
							<td>비밀번호</td>
							<td><input type="text" name="pass" id="login_pass" /></td>
						</tr>
						<tr>
							<td></td>
							<td><input type="submit" value="로그인" /></td>
						</tr>
					</table>
				</form>
			</article>
			<article id="article2">
				<form action="#" method="post" id="make_acc">
					<h2>[ 계좌개설 ]</h2>
					<br>
					<table>
						<tr>
							<td>계좌번호</td>
							<td><input type="text" name="accid" id="make_id" /></td>
						</tr>
						<tr>
							<td>이름</td>
							<td><input type="text" name="name" id="make_name" /></td>
						</tr>
						<tr>
							<td>입금액</td>
							<td><input type="text" name="money" id="make_money" /></td>
						</tr>
						<tr>
							<td>계좌구분</td>
							<td><input type="radio" value="normal" name="sect"
								checked="checked" /> 일반&nbsp;&nbsp;<input type="radio"
								value="special" name="sect" /> 특수</td>
						</tr>
						<tr>
							<td>등급</td>
							<td><select name="grade" class="in" disabled="disabled">
									<option value="V">VIP</option>
									<option value="G">Gold</option>
									<option value="S">Silver</option>
									<option value="N">Normal</option>
							</select></td>
						</tr>
						<tr>
							<td></td>
							<td colspan="2" style="text-align: right;"><input
								type="submit" value="개설" /></td>
						</tr>
					</table>
				</form>

			</article>
			<article id="article3">
				<form action="#" method="post" id="deposit">
					<h2>[ 입금 ]</h2>
					<br>
					<table>
						<tr>
							<td>계좌번호</td>
							<td><input type="text" name="accid" id="deposit_id" /></td>
						</tr>
						<tr>
							<td>입금액</td>
							<td><input type="text" name="money" id="deposit_money" /></td>
						</tr>
						<tr>
							<td></td>
							<td><input type="submit" value="입금" /></td>
						</tr>
					</table>
				</form>
			</article>

			<article id="article4">
				<form action="#" method="post" id="withdraw">
					<h2>[ 출금 ]</h2>
					<br>
					<table>
						<tr>
							<td>계좌번호</td>
							<td><input type="text" name="accid" id="withdraw_id" /></td>
						</tr>
						<tr>
							<td>출금액</td>
							<td><input type="text" name="money" id="withdraw_money" /></td>
						</tr>
						<tr>
							<td></td>
							<td><input type="submit" value="출금" /></td>
						</tr>
					</table>
				</form>
			</article>

			<article id="article5">
				<form action="#" method="post" id="acc_info">
					<h2>[ 계좌조회 ]</h2>
					<br>
					<table>
						<tr>
							<td>계좌번호</td>
							<td><input type="text" name="accid" id="acc_info_id" /></td>
						</tr>
						<tr>
							<td></td>
							<td><input type="submit" value="조회" /></td>
						</tr>
					</table>
				</form>
			</article>

			<article id="article6">
				<form action="#" method="post" id="all_acc_info">
					<h2>[ 전체계좌조회 ]</h2>
					<br>
					<table>
						<tr>
							<td width='250px'><input type="submit" value="조회" /></td>
						</tr>
					</table>
				</form>
			</article>
		</section>
	</div>
	<div class="container">
		<footer>Copyright (c) 2021 multicampus bank</footer>
	</div>
</body>
</html>
```



```css
* {
	padding: 0px;
	margin: 0px;
}

.container {
	width: 1080px;
	margin: 0 auto;
	margin-bottom: 8px;
	overflow: hidden;
}

a {
	text-decoration: none;
}

li {
	list-style: none;
	width: 140px;
	height: 70px;
	border: 7px solid #FFFFFF;
	border-radius: 30px;
	box-shadow: 5px 5px 5px #A9A9A9;
	background-color: gray;
}

li>a {
	display: block;
	line-height: 70px;
	text-align: center;
}

.account {
	float: left;
	padding: 8px 0;
}

.account>li {
	list-style-type: none;
	float: left;
	padding-left: 16px;
}

.login {
	float: right;
	padding-top: 8px;
	padding-bottom: 8px;
	padding-left: 0;
}

header {
	display: block;
	height: 100px;
	line-height: 100px;
	text-align: center;
	background-color: orange;
}

footer {
	display: block;
	height: 50px;
	line-height: 50px;
	text-align: center;
	background-color: gray;
}

article {
	background: silver;
	width: 1080px;
	height: 500px;
	padding: 30px;
	border: 2px;
}

h2 {
	text-align: center;
}

table {
	display: bolck;
	margin: 0 auto;
	width: 500;
	height: 500;
}

tr {
	height: 40px;
}

td {
	padding: 5px;
	text-align: center;
	font-size: 20px;
}

input[type=text], select {
	height: 35px;
	width: 100%;
	border-radius: 5px;
	font-size: 20px;
}

input[type=submit] {
	height: 45px;
	width: 100%;
	border-radius: 5px;
	font-size: 20px;
}

input[type=radio] {
	width: 20px;
	height: 20px;
	border: 1px;
}
```

