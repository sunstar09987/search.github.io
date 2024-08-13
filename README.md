<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>네이버 사전 동시 검색</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            height: 100vh;
            overflow: hidden;
        }

        #search-container {
            position: absolute;
            top: 20px;
            width: 100%;
            text-align: center;
        }

        input {
            width: 300px;
            padding: 10px;
            margin: 10px;
        }

        button {
            padding: 10px 20px;
        }

        .dictionary-container {
            display: flex;
            flex-direction: row;
            justify-content: center;
            align-items: flex-start;
            width: 100%;
            height: 100%;
            padding-top: 80px;
            box-sizing: border-box;
        }

        .dictionary {
            width: 33%;
            height: 100%;
            border: 1px solid #ccc;
            box-sizing: border-box;
        }

        h2 {
            font-size: 1.2em;
            margin: 10px 0;
            text-align: center;
        }

        iframe {
            width: 100%;
            height: calc(100% - 40px);
            border: none;
        }
    </style>
</head>
<body>
    <div id="search-container">
        <input type="text" id="searchTerm" placeholder="검색어를 입력하세요" onkeydown="if(event.key === 'Enter') search()">
        <button onclick="search()">검색</button>
    </div>

    <div class="dictionary-container">
        <div class="dictionary">
            <h2>네이버 영어사전</h2>
            <iframe id="englishDict"></iframe>
        </div>

        <div class="dictionary">
            <h2>네이버 국어사전</h2>
            <iframe id="koreanDict"></iframe>
        </div>

        <div class="dictionary">
            <h2>네이버 한자사전</h2>
            <iframe id="hanjaDict"></iframe>
        </div>
    </div>

    <script>
        function search() {
            const term = document.getElementById('searchTerm').value;
            if (term) {
                document.getElementById('englishDict').src = `https://endic.naver.com/search.nhn?sLn=kr&isOnlyViewEE=N&query=${term}`;
                document.getElementById('koreanDict').src = `https://ko.dict.naver.com/#/search?query=${term}`;
                document.getElementById('hanjaDict').src = `https://hanja.dict.naver.com/#/search?query=${term}`;
            }
        }
    </script>
</body>
</html>
