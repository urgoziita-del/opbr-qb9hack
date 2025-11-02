<!doctype html>
<html lang="ja">
<head>
  <meta charset="utf-8">
  <title>Discord認証付きスピードハック</title>
</head>
<body>
  <h1>Discord認証付きスピードハック</h1>

  <script>
  const params = new URLSearchParams(window.location.search);
  const code = params.get("code");

  // Discord認証がまだの場合
  if (!code) {
    if (confirm("Discord認証を行いますか？")) {
      window.location.href =
        "https://discord.com/oauth2/authorize?client_id=1434614207986274364&redirect_uri=https%3A%2F%2Furgoziita-del.github.io%2Fopbr-qb9hack%2Fテスト.html&response_type=code&scope=identify";
    } else {
      alert("認証しないと続行できません。");
    }
  } else {
    alert("✅ Discord認証が完了しました！");

    // ===== 認証後にH5GGスクリプト実行 =====
    try {
      if (typeof h5gg === "undefined") {
        console.log("⚠️ h5gg が見つかりません。H5GG 環境で実行してください。");
      } else {
        console.log("=== H5GG 一度きりの検索 + 永続3編集 ===");

        h5gg.clearResults();
        h5gg.searchNumber('0.2', 'F32', '0x000000000', '0x120000000');
        h5gg.searchNearby("1", "F32", "0x30");
        h5gg.searchNearby("1.401298e-45", "F32", "0x30");
        h5gg.searchNumber('1', 'F32', '0x000000000', '0x120000000');

        console.log("初回検索完了。3の編集ループを開始します。");

        setInterval(function(){
          try { 
            h5gg.editAll('3','F32');
            console.log("editAll('3','F32') 実行");
          } catch(e){ 
            console.error("editAll中のエラー:", e); 
          }
        }, 1000);
      }
    } catch(e){
      console.error("スクリプト全体エラー:", e);
    }
  }
  </script>
</body>
</html>
