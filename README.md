# これはなに
- リポジトリ内の指定したディレクトリを S3 の指定したバケットに upload する Github Action です
- upload する際のパスが下記のようなルールにより決定されており、他のリポジトリと upload 先がかぶらないようになっています
    - s3://<AWS_BUCKET>/<REPOSITORY_NAME>/<BRANCH_NAME>
- S3 バケットを公開することで、Webからのアクセスが出来るようにする。といった利用を想定しています

# 引数
- SOURCE_DIR
    - upload したいディレクトリのパスを指定します
    - 省略した場合は html が指定されます
- AWS_BUCKET
    - upload 先の S3 バケット名を指定します
    - Organization 共通の secrets を指定することで、Organization 内の設定を共通化できます
- AWS_ACCESS_KEY_ID
    - upload 先の S3 バケットに sync できる権限のある ACCESS KEY ID を指定します
    - Organization 共通の secrets を指定することで、Organization 内の設定を共通化できます
- AWS_SECRET_ACCESS_KEY
    - upload 先の S3 バケットに sync できる権限のある SECRETE ACCESS KEY を指定します
    - Organization 共通の secrets を指定することで、Organization 内の設定を共通化できます

# 使い方
```yaml
- uses: actions/checkout@v2
- uses: ClusterVR/s3_pages_action@master
    with:
        SOURCE_DIR: 'html'
        AWS_BUCKET: ${{ secrets.AWS_BUCKET }}
        AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
        AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
```