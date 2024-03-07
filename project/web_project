
from flask import Flask, request, render_template, redirect, url_for
import pymysql

app = Flask(__name__)

# 데이터베이스 연결 설정
db_config = {
    'host': '127.0.0.1',
    'user': 'root',
    'password': '0000',
    'db': 'testdb',
    'charset': 'utf8'
}

@app.route('/')
def form():
    # HTML 폼을 렌더링하는 라우트
    return render_template('index.html')

@app.route('/submit', methods=['POST'])
def submit():
    # 폼 데이터를 처리하는 라우트
    id = request.form['id']
    name = request.form['name']
    
    # 데이터베이스에 데이터 삽입
    connection = pymysql.connect(**db_config)
    try:
        with connection.cursor() as cursor:
            sql = "INSERT INTO testdb (id, name) VALUES (%s, %s)"
            cursor.execute(sql, (id, name))
        connection.commit()
    finally:
        connection.close()
    
    return redirect('/')

if __name__ == '__main__':
    app.run(debug=True)
