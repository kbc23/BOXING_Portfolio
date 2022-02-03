# 「BOXING!!!」ポートフォリオ
河原電子ビジネス専門学校　ゲームクリエイター科２年（2022年2月時点）  
氏名：塚野博士  
<br>


---
# 目次
* [目次](#目次)
* [1. 作品概要](#1-作品概要)
* [2. 担当箇所](#2-担当箇所)
    * [2.1. 担当したソースコード](#21-担当したソースコード)
    * [2.2. 担当した仕様](#22-担当した仕様)
* [3. 改造したエンジンコード](#3-改造したエンジンコード)
* [4. ゲーム内容](#4-ゲーム内容)
* [5. 操作説明](#5-操作説明)
* [6. 技術紹介](#6-技術紹介)
    * [6.1. ネットワーク対戦](#61-ネットワーク対戦)
    * [6.2. ボーンを利用した処理「スウェー」](#62-ボーンを利用した処理スウェー)
    * [6.3. ボーンを利用した処理「当たり判定」](#63-ボーンを利用した処理当たり判定)
    * [6.4. インスタンシング描画](#64-インスタンシング描画)
    * [6.5. csvファイルの読み込み](#65-csvファイルの読み込み)
* [7. ゲーム的にこだわったところ](#7-ゲーム的にこだわったところ)
    * [7.1. しゃがみ](#71-しゃがみ)
    * [7.2. スウェーの滑らかさ](#72-スウェーの滑らかさ)
    * [7.3. 攻撃判定と当たり判定](#73-攻撃判定と当たり判定)


---
# 1. 作品概要
* タイトル  
BOXING!!!
* 学校  
河原電子ビジネス専門学校
* 制作人数  
１人
* 制作期間  
2021年10月～2022年1月（現在進行形）
* ゲームジャンル  
格闘ゲーム
* プレイ人数  
２人
* 対応ハード  
PC（Windows10）
* 対応コントローラー  
キーボード、ゲームパッド
* 使用言語  
C++、HLSL
* 開発環境
    * エンジン  
    tkEngineMini（学校内製の簡易エンジン）  
    URL https://github.com/KawaharaKiyohara/tkEngineMini
    * プログラム  
    Visual Studio 2019
    * 3Dモデル、アニメーション  
    3ds MAX
    * 画像  
    <!--FireAlpaca-->
    * バージョン管理  
    GitHub
    * タスク管理  
    Redmine
    * 連絡手段  
    Slack
* GitHub  
URL https://github.com/kbc23/FightingGame
* 備考


---
# 2. 担当箇所
## 2.1. 担当したソースコード
* cppファイル、hファイル
    * game_data[cpp][h]<br>
    ゲームデータを保管しているファイル<br>
    * game[cpp][h]<br>
    ゲームのメインの流れを書いているファイル<br>
    * actor[cpp][h]<br>
    モデルの位置、回転、拡大情報などを管理しているファイル<br>
    * player_UI[cpp][h]<br>
    UIのデータ管理しているファイル<br>
    * player_camera[cpp][h]<br>
    プレイヤーのカメラの処理を書いているファイル<br>
    * player[cpp][h]<br>
    プレイヤー関連の処理を書いているファイル<br>
    * hitbox[cpp][h]<br>
    当たり判定のボックスの処理を書いているファイル<br>
    * st_attack_data[cpp][h]<br>
    プレイヤーの攻撃関連の情報が書かれているファイル<br>
    * st_defence_data[cpp][h]<br>
    プレイヤーの防御関連の情報が書かれているファイル<br>
    * st_player_status[cpp][h]<br>
    プレイヤーの情報を管理しているファイル<br>
    * audience[cpp][h]<br>
    観客の処理が書かれているファイル<br>
    * read_CSV_file[cpp][h]<br>
    csvファイルを読み込む処理を書いているファイル<br>
    * read_CSV_file_character_data[dpp][h]<br>
    キャラクター関係のデータをcsvファイルから読み込む処理が書いているファイル<br>
    * net_work[cpp][h]<br>
    ネットワークの処理が書いているファイル<br>
    * model_render[cpp][h]<br>
    モデルの描画処理が書いているファイル<br>
    * shadow[cpp][h]<br>
    モデルの影の描画処理が書いているファイル<br>
    * shadow_light_camera[cpp][h]<br>
    モデルの影を描画するのに使用するカメラの処理が書いているファイル。<br>
    * shadow_map[cpp][h]<br>
    モデルの影用のレンダリングターゲットを作成する処理が書いているファイル。<br>
    * font_render[cpp][h]<br>
    文字の描画の処理が書いているファイル。<br>
    * debug_wire_frame[cpp][h]<br>
    当たり判定のボックスを確認するためのファイル。<br>
    * my_debug[cpp][h]<br>
    ネットワークに繋がない状態で確認するためのファイル<br>


---
## 2.2. 担当した仕様
<!--
* タイトルシーン
* モード選択シーン
* プレイヤー人数選択シーン
* CPUの強さ選択シーン
* ゲームシーンの一部
    * プレイヤー
    * ステージ
    * スコア（プレイヤーのタイム）
    * ゲーム開始時のカウントダウン
-->

---
# 3. 改造したエンジンコード
* cppファイル、hファイル
<!--
    * Material.cpp  
    30～38行、80行
    * Material.h  
    43～50行、111行、115行
    * MeshParts.cpp  
    71、72行
    * NullTextureMaps.cpp  
    41～46行
    * NullTextureMaps.h  
    41～56行、125、126行
    * TkmFile.h
    30、31行
* fxファイル
    * model.fx
-->

---
# 4. ゲーム内容
ボコスカ殴り合って、相手を先に３回ダウンさせるか、１０カウントさせたら勝利のボクシングゲーム。


---
# 5. 操作説明
## キーボード
* 選択画面（後で対応キーを変更）

* ゲーム画面

## ゲームパッド
* ゲーム画面

---
# 6. 技術紹介
## 6.1. ネットワーク対戦
photonを使用し、C++でネットワークの処理を作成。

---
## 6.2. ボーンを利用した処理「スウェー」
ボクシングのスウェーをおこなう際、モデルのボーンを回転させておこなっている。

### 処理の流れ
1. 右スティックの入力に応じて、スウェーの移動方向を取得。
2. ボーンの名前で検索し、該当するボーンのボーンIDを取得する。<br>
```cpp
	// 骨の名前でボーンIDを検索
	int boneId = m_skeletonPointer->FindBoneID(L"J_Bip_C_UpperChest");
```
3. 検索して取得したボーンIDから、ボーンを取得。<br>
```cpp
	// 検索したボーンIDを使用して、ボーンを取得
	Bone* bone = m_skeletonPointer->GetBone(boneId);
```
4. ボーンのローカル行列を取得。<br>
```cpp
	// ボーンのローカル行列を取得
	Matrix boneMatrix = bone->GetLocalMatrix();
```
5. 先ほど取得したスウェーの移動方向を使い、このフレームでのボーンの回転する方向と量を決める。
```cpp
	// ボーンの回転の軸になる前方向のベクトルを作成
	Vector3 vecFront = Vector3::Front;
	// ボーンの回転の軸になる右方向のベクトルを作成
	Vector3 vecRight = Vector3::Right;
	// ボーンの回転の軸に使用するベクトルをY軸に回すためのクォータニオンを作成
	Quaternion m_RotY;
	m_RotY.SetRotationY(0.6f); // 回転量を設定
	// ボーンの回転の軸になるベクトルをY軸で回転
	m_RotY.Apply(vecFront);
	m_RotY.Apply(vecRight);

	// スウェーの移動量を計算
	CheckSwayMove();
```
```cpp
void ModelRender::CheckSwayMove()
{
	// 左右方向の移動量の計算
	// 入力: 左
	if (EnSwayController::enLeft == m_swayController[EnXY::x]) {
		m_swayMove.x -= SWAY_MOVE;

		// 移動量が上限を超えたか
		if (EnSwayController::enLeft >= m_swayMove.x) {
			m_swayMove.x = EnSwayController::enLeft;
		}
	}
	// 入力: 右
	else if (EnSwayController::enRight == m_swayController[EnXY::x]) {
		m_swayMove.x += SWAY_MOVE;

		// 移動量が上限を超えたか
		if (EnSwayController::enRight <= m_swayMove.x) {
			m_swayMove.x = EnSwayController::enRight;
		}
	}
	// 入力: なし
	else if (EnSwayController::enNotMove == m_swayController[EnXY::x]) {
		// 右方向に移動している
		if (EnSwayController::enNotMove < m_swayMove.x) {
			m_swayMove.x -= SWAY_MOVE;

			// 逆側に移動したか
			if (EnSwayController::enNotMove > m_swayMove.x) {
				m_swayMove.x = EnSwayController::enNotMove;
			}
		}
		// 左方向に移動している
		else if (EnSwayController::enNotMove > m_swayMove.x) {
			m_swayMove.x += SWAY_MOVE;

			// 逆側に移動したか
			if (EnSwayController::enNotMove < m_swayMove.x) {
				m_swayMove.x = EnSwayController::enNotMove;
			}
		}
	}

	// 上下方向の移動量の計算
	// 入力: 上
	if (EnSwayController::enUp == m_swayController[EnXY::y]) {
		m_swayMove.y += SWAY_MOVE;

		// 移動量が上限を超えたか
		if (EnSwayController::enUp <= m_swayMove.y) {
			m_swayMove.y = EnSwayController::enUp;
		}
	}
	// 入力: 下
	else if (EnSwayController::enDown == m_swayController[EnXY::y]) {
		m_swayMove.y -= SWAY_MOVE;

		// 移動量が上限を超えたか
		if (EnSwayController::enDown >= m_swayMove.y) {
			m_swayMove.y = EnSwayController::enDown;
		}
	}
	// 入力: なし
	else if (EnSwayController::enNotMove == m_swayController[EnXY::y]) {
		// 上方向に移動している
		if (EnSwayController::enNotMove < m_swayMove.y) {
			m_swayMove.y -= SWAY_MOVE;

			// 逆側に移動したか
			if (EnSwayController::enNotMove > m_swayMove.y) {
				m_swayMove.y = EnSwayController::enNotMove;
			}
		}
		// 下方向に移動している
		else if (EnSwayController::enNotMove > m_swayMove.y) {
			m_swayMove.y += SWAY_MOVE;

			// 逆側に移動したか
			if (EnSwayController::enNotMove < m_swayMove.y) {
				m_swayMove.y = EnSwayController::enNotMove;
			}
		}
	}
}
```
6. ボーンを回転させる。
```cpp
	// ボーンの回転情報を作成する行列を作成
	Matrix rotMatrixX, rotMatrixZ;
	// 回転情報を作成
	rotMatrixX.MakeRotationAxis(vecFront, -m_swayMove.x);
	rotMatrixZ.MakeRotationAxis(vecRight, m_swayMove.y);

	// 回転情報の行列を乗算し、ボーンを回転させる
	rotMatrixX *= rotMatrixZ;
	boneMatrix *= rotMatrixX;
```
7. 回転したボーンの情報をローカル行列に設定。
```cpp
	// 変更したボーン行列を設定
	bone->SetLocalMatrix(boneMatrix);
```
8. モデルを描画。

---
## 6.3. ボーンを利用した処理「当たり判定」
当たり判定は、ボックスを作っているが、モデルのボーンを利用し身体の部位ごとに作っている。

### 処理の流れ
1. 身体の部位ごとのボックスが保持できる配列を用意。
```cpp
    // 身体のパーツすべてが入る配列のサイズを確保
    m_ghostBox.resize(EnBodyParts::enMaxBodyParts);

    // ポインタを作成
    for (int bodyPartsNum = 0; EnBodyParts::enMaxBodyParts > bodyPartsNum; ++bodyPartsNum) {
        m_ghostBox[bodyPartsNum].reset(new GhostObject);
    }
```
2. スケルトンの情報が取得できたら、スケルトンのそれぞれのボーンを利用して当たり判定のボックスを作成する。<br>
    1. ボーンの名前で検索し、該当するボーンのボーンIDを取得する。<br>
    ```cpp
        // 骨の名前でボーンIDを検索
        int boneId = m_getActor->GetSkeleton().FindBoneID(BONE_NAME[bodyPartsNum]);
    ```
    2. 検索して取得したボーンIDから、ボーンを取得。<br>
    ```cpp
        // 検索したボーンIDを使用して、ボーンを取得
        Bone* bone = m_getActor->GetSkeleton().GetBone(boneId);
    ```
    3. ボーンのローカル行列を取得。
    ```cpp
        // ボーンのワールド行列を取得
        Matrix boneMatrix = bone->GetWorldMatrix();
    ```
    4. 取得したローカル行列からボーンの位置情報、回転情報を取得。<br>
    ```cpp
        // 行列から位置情報を取得
        Vector3 boxPos = boneMatrix.GetTranslation();
        
        // 行列から回転情報を取得
        Quaternion boxRot = Quaternion::Identity;
        boxRot.SetRotation(boneMatrix);
    ```
    5. ボーンの位置情報をボックスの位置情報に使用する際、すこし調整をおこなう。
    ```cpp
        // 位置の調整
        Vector3 boxPositionAdjustment = HITBOX_POSITION_ADJUSTMENT[bodyPartsNum];
        boxRot.Apply(boxPositionAdjustment);
        boxPos += boxPositionAdjustment;
    ```
    6. 取得したボーンの位置情報、回転情報を使って当たり判定のボックスを作成。
    ```cpp
        // 当たり判定を作成
        m_ghostBox[bodyPartsNum]->CreateBox(boxPos, boxRot, HITBOX_SIZE[bodyPartsNum]);
    ```
3. 作成した後、毎フレーム位置、回転情報を更新する。
    1. ボーンの名前で検索し、該当するボーンのボーンIDを取得する。<br>
    ```cpp
        // 骨の名前でボーンIDを検索
        int boneId = m_getActor->GetSkeleton().FindBoneID(BONE_NAME[bodyPartsNum]);
    ```
    2. 検索して取得したボーンIDから、ボーンを取得。<br>
    ```cpp
        // 検索したボーンIDを使用して、ボーンを取得
        Bone* bone = m_getActor->GetSkeleton().GetBone(boneId);
    ```
    3. ボーンのローカル行列を取得。
    ```cpp
        // ボーンのワールド行列を取得
        Matrix boneMatrix = bone->GetWorldMatrix();
    ```
    4. 取得したローカル行列からボーンの位置情報、回転情報を取得。<br>
    ```cpp
        // 行列から位置情報を取得
        Vector3 boxPos = boneMatrix.GetTranslation();

        // 行列から回転情報を取得
        Quaternion boxRot = Quaternion::Identity;
        boxRot.SetRotation(boneMatrix);
    ```
    5. ボーンの位置情報をボックスの位置情報に使用する際、すこし調整をおこなう。
    ```cpp
        // 位置の調整
        Vector3 boxPositionAdjustment = HITBOX_POSITION_ADJUSTMENT[bodyPartsNum];
        boxRot.Apply(boxPositionAdjustment);
        boxPos += boxPositionAdjustment;
    ```
    6. 取得したボーンの位置情報、回転情報を使って当たり判定のボックスの情報を更新。
    ```cpp
        // 当たり判定の情報を更新
        m_ghostBox[bodyPartsNum]->UpdateGhostObject(boxPos, boxRot);
    ```



---
## 6.4. インスタンシング描画
このゲームでは、観客をインスタンシング描画で描画している。

### 処理の流れ
1. ModelRenderクラスに描画するモデルのインスタンスの数を投げる。（引数で投げている）
```cpp
    void ModelRender::InitInstancingModel(
        const char* filePath,
        const int modelMaxNum, // インスタンスの数
        modelUpAxis::EnModelUpAxis modelUpAxis
    )
    {
        // インスタンスの数をセット
        m_instancing.m_instanceNum = modelMaxNum;
```
2. インスタンスの数だけのモデルの座標、回転、拡大情報を初期化。
```cpp
	// モデルの座標を初期化
	m_instancing.m_position = new Vector3[m_instancing.m_instanceNum];
	m_instancing.m_rotation = new Quaternion[m_instancing.m_instanceNum];
	m_instancing.m_scale = new Vector3[m_instancing.m_instanceNum];

	// モデルの座標、回転、拡大率を初期化
	for (int instanceNum = 0; instanceNum < m_instancing.m_instanceNum; instanceNum++) {
		// インスタンス全ての座標を原点、回転をデフォルト、拡大率を１倍に設定
		m_instancing.m_position[instanceNum] = Vector3::Zero;
		m_instancing.m_rotation[instanceNum] = Quaternion::Identity;
		m_instancing.m_scale[instanceNum] = Vector3::One;
	}
```
3. インスタンスの数分のワールド行列をcpp側で計算して記憶しておくための行列の配列の確保と、そのデータをグラフィックメモリに送るためのストラクチャードバッファの確保をおこなう。
```cpp
	// インスタンシング描画のワールド?列関係の各種バッファを確保
	// まずは計算?のバッファをメインメモリ上に確保する
	m_instancing.m_worldMatrixArray = new Matrix[m_instancing.m_instanceNum];
	// 続いて、シェーダー側でワールド?列を使?するためのストラクチャードバッファをVRAM上に確保する
	m_instancing.m_worldMatrixSB.Init(
		sizeof(Matrix),
		m_instancing.m_instanceNum,
		nullptr
	);
```
4. インスタンシング描画をおこなうモデルの初期化。拡張SRVにストラクチャードバッファを渡す。
```cpp
	// モデルの初期化データを設定する
	ModelInitData modelInitData;

	// tkmファイルのパスを指定
	modelInitData.m_tkmFilePath = "Assets/modelData/model/model.tkm";
	// 使?するシェーダーファイルのパスを指定
	modelInitData.m_fxFilePath = "Assets/shader/Instancing.fx";
	// 拡張SRVにストラクチャードバッファを渡す
	modelInitData.m_expandShaderResoruceView[0] = &m_instancing.m_worldMatrixSB;

	// スケルトンを指定する
	if (m_skeletonPointer) {	// スケルトンが初期化されていたら
		modelInitData.m_skeleton = m_skeletonPointer.get();
	}
	// モデルの上方向を指定
	modelInitData.m_modelUpAxis = modelUpAxis;

	// 設定したデータでモデルを初期化
	m_model.Init(modelInitData);
```
5. ワールド行列を計算する。
```cpp
	// ワールド?列を計算する
	for (int instanceNum = 0; instanceNum < m_instancing.m_instanceNum; instanceNum++) {
		m_instancing.m_worldMatrixArray[instanceNum] =
			m_model.CalcWorldMatrix(
				m_instancing.m_position[instanceNum],
				m_instancing.m_rotation[instanceNum],
				m_instancing.m_scale[instanceNum]
			);
	}
```
6. ワールド行列の内容をグラフィックメモリにコピーする。
```cpp
	// ワールド?列の内容をグラフィックメモリにコピー
	m_instancing.m_worldMatrixSB.Update(m_instancing.m_worldMatrixArray);
```
7. モデルをインスタンシング描画する。
```cpp
	// インスタンシング描画
	m_model.DrawInstancing(renderContext, m_instancing.m_instanceNum);
```



---
## 6.5. csvファイルの読み込み
csvファイルにファイルパスを記載し、それをコード側で読み込む手法を取っている。

### 処理の流れ（セル番号指定）
1. csvファイルを開く。
```cpp
    // ファイルを開く
    Open(filePath);
```
```cpp
const bool ReadCSVFile::Open(const std::string& openFile)
{
	// すでに開いている
	if (true == IsOpen()) {
		return false;
	}

	// ファイルパスを保持
	m_filePath = openFile;
	// ファイルを開く
	m_file.open(m_filePath);

	// ファイルが開けなかったときの処理
	if (!m_file) {
		return false;
	}

	return true;
}
```
2. 指定した番号の行全体の文字列を取得。
3. 行全体の文字列から、カンマで文字列を区切り、指定した番号の文字列を取得。
```cpp
    // キャラクターモデルのファイルネームを取得
    m_characterModelPath = GetCell(2, 2);
```
```cpp
std::string ReadCSVFile::GetCell(const int xCell, const int yCell)
{
	if (false == IsOpen()) {
		return m_NOT_FOUND;
	}

	// セルの指定で０以下を指定している場合
	if (con::NG_LESS_THAN_CELL_SPECIFICATION >= xCell ||
		con::NG_LESS_THAN_CELL_SPECIFICATION >= yCell) {
		return m_NOT_FOUND;
	}

	std::string getlineYStr; // Y軸の行のgetline()で使用する変数
	std::string cellStr; // 取得したセルの文字列を保管する変数

	// 指定した行を検索
	for (int checkYNum = con::FIRST_OF_THE_ARRAY; checkYNum < yCell; checkYNum++) {
		// 指定した行が見つからない場合
		if (true == m_file.eof()) {
			// csvファイルの読み取り位置をファイルの先頭に移動する
			m_file.seekg(con::FIRST_OF_THE_READING_POSITION, std::ios_base::beg);

			return m_NOT_FOUND;
		}

		// 行のデータを取得
		std::getline(m_file, getlineYStr);
	}

	std::stringstream YLineStr(getlineYStr); // 取得した行のデータを保管する変数

	// 見つけた行から指定したセルを検索
	for (int checkCellNum = con::FIRST_OF_THE_ARRAY; checkCellNum < xCell; checkCellNum++) {
		// 指定したセルが見つからない場合
		if (true == YLineStr.eof()) {
			// csvファイルの読み取り位置をファイルの先頭に移動する
			m_file.seekg(con::FIRST_OF_THE_READING_POSITION, std::ios_base::beg);

			return m_NOT_FOUND;
		}

		// セルのデータを取得
		std::getline(YLineStr, cellStr, con::CELL_DELIMITER);
	}

	// csvファイルの読み取り位置をファイルの先頭に移動する
	m_file.seekg(con::FIRST_OF_THE_READING_POSITION, std::ios_base::beg);

	// セルのデータが空の場合
	if (con::EMPTY_CELL == cellStr) {
		return m_NOT_FOUND;
	}

	return cellStr;
}
```


### 処理の流れ（指定の文字列がある行全体を読み込む）
1. csvファイルを開く。
```cpp
    // ファイルを開く
    Open(filePath);
```
```cpp
const bool ReadCSVFile::Open(const std::string& openFile)
{
	// すでに開いている
	if (true == IsOpen()) {
		return false;
	}

	// ファイルパスを保持
	m_filePath = openFile;
	// ファイルを開く
	m_file.open(m_filePath);

	// ファイルが開けなかったときの処理
	if (!m_file) {
		return false;
	}

	return true;
}
```
2. 指定した文字列が存在する行を検索。
3. 指定した文字列が存在する行全体の文字列を取得。
4. 行全体の文字列をカンマで区切り、それぞれを配列で取得する。
```cpp
    // アニメーションデータのファイルネームを取得
    GetLineByWord("アニメーション", m_characterAnimationPath);
```
```cpp
void ReadCSVFile::GetLineByWord(const std::string& checkWord, std::vector<std::string>& arrayStr)
{
	if (false == IsOpen()) {
		arrayStr.push_back(m_NOT_FOUND);

		return;
	}

	std::string getlineYStr; // Y軸の行のgetline()で使用する変数
	std::string cellStr; // 取得したセルの文字列を保管する変数
	bool flagWordMatch = false; // 指定した文字列と同じ文字列があったか

	// 指定したキーワードと一致するセルがある行を検索
	while (std::getline(m_file, getlineYStr)) {
		// 最初にcsvファイルの一文を抜き出す
		// getlineで抜き出せるようにするためにstringstream型の変数に入れる
		std::stringstream YLineStr(getlineYStr); // 取得した行のデータを保管する変数

		// 一致する文字列があるか検索
		while (std::getline(YLineStr, cellStr, con::CELL_DELIMITER)) {
			// 一致する文字列があった場合
			if (checkWord == cellStr) {
				flagWordMatch = true;

				break;
			}
		}

		// 一致する文字列があった場合
		if (true == flagWordMatch) {
			//std::stringstream r_str(getlineYStr);

			// 文字列の先頭の位置にカーソルを移動
			YLineStr.seekg(con::FIRST_OF_THE_READING_POSITION, std::ios_base::beg);

			// vector配列に格納する
			while (std::getline(YLineStr, cellStr, con::CELL_DELIMITER)) {
				// データが空のセルがあった場合
				if (con::EMPTY_CELL == cellStr) {
					break;
				}

				// セルのデータを末尾に追加
				arrayStr.push_back(cellStr);
			}

			// csvファイルの読み取り位置をファイルの先頭に移動する
			m_file.seekg(con::FIRST_OF_THE_READING_POSITION, std::ios_base::beg);

			return;
		}
	}

	// 一致する文字列がなかった場合
	arrayStr.push_back(m_NOT_FOUND);

	// csvファイルの読み取り位置をファイルの先頭に移動する
	m_file.seekg(con::FIRST_OF_THE_READING_POSITION, std::ios_base::beg);
}
```




---
# 7. ゲーム的にこだわったところ
## 7.1. しゃがみ
前方向へのスウェーより、しゃがんだ方が攻撃を回避できるのではないかと考え、スウェーの入力で前方向に入力した際、スウェーをするのではなくしゃがむようになっている。<br>
（このしゃがみはアニメーションでおこなっている）

---
## 7.2. スウェーの滑らかさ
スウェーの動きを滑らかにし、自然な動きにしている。<br>
スウェーの移動量を計算する際、取得していたスウェーの移動方向に対し、一定値を加算することに滑らかな動きにしている。<br>
また、ここで移動量の上限を設定しておき、上限以上に移動しないようにしている。
```cpp
namespace // constant
{
	const float SWAY_MOVE = 0.2f; // １フレームのスウェーの移動量
}

void ModelRender::CheckSwayMove()
{
	// 左右方向の移動量の計算
	// 入力: 左
	if (EnSwayController::enLeft == m_swayController[EnXY::x]) {
		m_swayMove.x -= SWAY_MOVE;

		// 移動量が上限を超えたか
		if (EnSwayController::enLeft >= m_swayMove.x) {
			m_swayMove.x = EnSwayController::enLeft;
		}
	}
	// 入力: 右
	else if (EnSwayController::enRight == m_swayController[EnXY::x]) {
		m_swayMove.x += SWAY_MOVE;

		// 移動量が上限を超えたか
		if (EnSwayController::enRight <= m_swayMove.x) {
			m_swayMove.x = EnSwayController::enRight;
		}
	}
	// 入力: なし
	else if (EnSwayController::enNotMove == m_swayController[EnXY::x]) {
		// 右方向に移動している
		if (EnSwayController::enNotMove < m_swayMove.x) {
			m_swayMove.x -= SWAY_MOVE;

			// 逆側に移動したか
			if (EnSwayController::enNotMove > m_swayMove.x) {
				m_swayMove.x = EnSwayController::enNotMove;
			}
		}
		// 左方向に移動している
		else if (EnSwayController::enNotMove > m_swayMove.x) {
			m_swayMove.x += SWAY_MOVE;

			// 逆側に移動したか
			if (EnSwayController::enNotMove < m_swayMove.x) {
				m_swayMove.x = EnSwayController::enNotMove;
			}
		}
	}

	// 上下方向の移動量の計算
	// 入力: 上
	if (EnSwayController::enUp == m_swayController[EnXY::y]) {
		m_swayMove.y += SWAY_MOVE;

		// 移動量が上限を超えたか
		if (EnSwayController::enUp <= m_swayMove.y) {
			m_swayMove.y = EnSwayController::enUp;
		}
	}
	// 入力: 下
	else if (EnSwayController::enDown == m_swayController[EnXY::y]) {
		m_swayMove.y -= SWAY_MOVE;

		// 移動量が上限を超えたか
		if (EnSwayController::enDown >= m_swayMove.y) {
			m_swayMove.y = EnSwayController::enDown;
		}
	}
	// 入力: なし
	else if (EnSwayController::enNotMove == m_swayController[EnXY::y]) {
		// 上方向に移動している
		if (EnSwayController::enNotMove < m_swayMove.y) {
			m_swayMove.y -= SWAY_MOVE;

			// 逆側に移動したか
			if (EnSwayController::enNotMove > m_swayMove.y) {
				m_swayMove.y = EnSwayController::enNotMove;
			}
		}
		// 下方向に移動している
		else if (EnSwayController::enNotMove > m_swayMove.y) {
			m_swayMove.y += SWAY_MOVE;

			// 逆側に移動したか
			if (EnSwayController::enNotMove < m_swayMove.y) {
				m_swayMove.y = EnSwayController::enNotMove;
			}
		}
	}
}
```

---
## 7.3. 攻撃判定と当たり判定
攻撃判定が当たり判定に当たった際、頭の当たり判定だったときダメージ量やダメージアニメーションが変わるようになっている。<br>
（攻撃判定は、プレイヤーの左手と右手の当たり判定を攻撃判定として利用している）

### 処理の流れ
1. 相手プレイヤーの当たり判定全体をfor文で自分の左手、右手の攻撃判定（当たり判定）に当たったかを確認する。
2. 自身の攻撃判定が当たっている相手プレイヤーの当たり判定が見つかった場合、相手プレイヤーの頭の当たり判定に当たったかを確認した後、for文から抜ける。
```cpp
    int checkHitBodyParts = EnBodyParts::enMaxBodyParts; // 当たり判定と攻撃判定が触れているか

    //プレイヤーの当たり判定と攻撃判定が触れたかの判定
    for (int bodyPartsNum = 0; EnBodyParts::enMaxBodyParts > bodyPartsNum; ++bodyPartsNum) {
        PhysicsWorld::GetInstance()->ContactTest(&m_getOtherPlayer->GetGhostObject(bodyPartsNum),
            [&](const btCollisionObject& contactObject)
            {
                // 左手が当たったとき
                if (m_ghostBox[EnBodyParts::enLeftHand]->IsSelf(contactObject)) {
                    checkHitBodyParts = bodyPartsNum;
                    return;
                }
                // 左手が当たったとき
                else if (m_ghostBox[EnBodyParts::enRightHand]->IsSelf(contactObject)) {
                    checkHitBodyParts = bodyPartsNum;
                    return;
                }
            });

        // 当たったら判定処理から抜ける
        if (EnBodyParts::enMaxBodyParts != checkHitBodyParts) {
            if (EnBodyParts::enHead == checkHitBodyParts) {
                m_damageStatus = EnDamageStatus::enHeadDamage;
            }
            else {
                m_damageStatus = EnDamageStatus::enBodyDamage;
            }

            break;
        }
    }
```