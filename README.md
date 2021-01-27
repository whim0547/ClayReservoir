# ClayReservoir

仮想粘土の粒子ベース・ビジュアルシミュレーション(小田ら, 2001, [paper](https://iwate-u.repo.nii.ac.jp/?action=repository_action_common_download&item_id=9993&item_no=1&attribute_id=36&file_no=1))を粒子の情報をもとにReservoirComputingで動かせないか試したもの

## 実行環境
Google Colab

## ファイル
- clay_particle.ipynb: 小田ら(2001)の粘土モデル
- reservoir_computing.ipynb: ReservoirComputing + テスト(テスト用に同じ粘土モデルを定義しているのは内緒)
- particle_test_data.npy, particle_test_data2.npy: 試しに作ってみた(そしてオチに至った)テストデータ
  - size: 情報種 * データ番号 * フレーム * 粒子 * 座標(4 * N * F * 400 * 2)
  - 情報種: input(pos, init move)&output(pos, final move(=posのdiff))の順で4つ
  - データ番号: 何個目のデータセットか(N)
  - フレーム: 何フレーム目の動作か(F)
  - 粒子: 何番目の粒子か(400)
  - 座標: Vector2

## オチ
ダイナミックな変形をしないと変形しないような学習をする

学習データの生成に時間がかなりかかる
- 要GPUプログラミング

粘土モデルがたまに不安定()
