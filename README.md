<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>汎用的合算機</title>
    <style>
        body { font-family: sans-serif; padding: 20px; background: #f0f2f5; line-height: 1.6; }
        .container { background: white; padding: 25px; border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.1); max-width: 500px; margin: auto; }
        h2 { color: #333; font-size: 1.2em; text-align: center; }
        textarea { width: 100%; height: 150px; padding: 10px; border: 2px solid #ddd; border-radius: 8px; box-sizing: border-box; font-size: 16px; resize: vertical; }
        textarea:focus { border-color: #007bff; outline: none; }
        .result-box { background: #e9ecef; margin-top: 20px; padding: 15px; border-radius: 8px; text-align: center; }
        .total-label { font-size: 0.9em; color: #666; }
        #total-result { display: block; font-size: 2em; font-weight: bold; color: #007bff; }
        .hint { font-size: 0.8em; color: #888; margin-top: 10px; }
    </style>
</head>
<body>

<div class="container">
    <h2>汎用的合算機</h2>
    <p class="hint">メモをそのまま貼り付けろ！数字だけ合計するぜ！</p>
    
    <textarea id="text-input" placeholder="例：&#13;&#10;各ワーク&#13;&#10;国5&#13;&#10;数23&#13;&#10;英32"></textarea>

    <div class="result-box">
        <span class="total-label">合計</span>
        <span id="total-result">0</span>
    </div>
</div>

<script>
    const textInput = document.getElementById('text-input');
    const resultDisp = document.getElementById('total-result');

    textInput.addEventListener('input', () => {
        const text = textInput.value;
        
        // 正規表現で「数字（連続したもの）」をすべて抜き出す
        // 半角・全角の両方に対応させるために一旦変換してもいいが、
        // 基本的な半角数字を対象にするぜ
        const numbers = text.match(/\d+/g); 

        let sum = 0;
        if (numbers) {
            sum = numbers.reduce((acc, curr) => acc + parseInt(curr, 10), 0);
        }

        // 3桁区切りのカンマを入れて表示
        resultDisp.textContent = sum.toLocaleString();
    });
</script>

</body>
</html>
