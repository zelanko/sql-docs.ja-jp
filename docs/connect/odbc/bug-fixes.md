---
title: 修正されたバグのリスト |Microsoft Docs
ms.custom: ''
ms.date: 06/29/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
author: v-makouz
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: 9dba11c0130dc3b969a9fcec46b631abd7d62fe8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63198766"
---
# <a name="list-of-bugs-fixed"></a>修正されたバグの一覧

このページには、以降では、各リリースで修正されたバグの一覧が含まれています[!INCLUDE[msCoName](../../includes/msconame_md.md)]ODBC Driver 17 for。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-173-for-includessnoversionincludesssnoversion-mdmd"></a>バグ修正、[!INCLUDE[msCoName](../../includes/msconame_md.md)]の ODBC ドライバー 17.3 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- 固定 TCP 送信通知イベント ハンドル メモリ リーク
- 列挙型 _SQL_FILESTREAM_DESIRED_ACCESS 内 msodbcsql.h ヘッダー ファイルの再定義は固定の問題
- 不足している固定の ACCESS_TOKEN および認証関連の Linux 用内 msodbcsql.h ヘッダー ファイルの定義

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-172-for-includessnoversionincludesssnoversion-mdmd"></a>バグ修正、[!INCLUDE[msCoName](../../includes/msconame_md.md)]の ODBC ドライバー 17.2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Azure Active Directory 認証に関するエラー メッセージを修正しました
- エンコードの検出が異なるロケールの環境変数が設定されている場合を修正しました
- 固定接続回復が進行中の接続を切断する時にクラッシュ
- 接続の存続性の検出を修正しました
- 閉じているソケットの不適切な検出を修正しました
- 失敗した回復中に、ステートメント ハンドルを解放しようとしています。 ときに、無期限の待機を修正しました
- バージョン 13 と 17 の両方が Windows にインストールされている場合、アンインストールが正しくない動作を修正
- 以前の Windows プラットフォーム (Windows 7、8、および Server 2012) に固定の復号化の動作
- Windows 上の ADAL 認証を使用する場合は、キャッシュの問題を修正しました
- ロックされた問題が修正し、Windows 上のログ トレースの上書き

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversion-mdmd"></a>バグ修正、[!INCLUDE[msCoName](../../includes/msconame_md.md)]の ODBC ドライバー 17.1 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- SQLFreeHandle を MARS を有効になっていると接続属性を呼び出すときに、1 秒の遅延を固定"Encrypt = [はい]"
- SQLGetData で渡されたバッファーのサイズが小さい場合、取得されるデータ (Windows) で、エラー 22003 クラッシュを修正しました
- 切り捨てられた ADAL エラー メッセージを修正しました
- 整数を小数点数の浮動に変換するときに、32 ビット Windows のまれなバグを修正しました
- Always Encrypted での 10 進数のフィールドに double を挿入してデータの切り捨てエラーを返すは、問題を修正しました
- MacOS のインストーラーに関する警告を修正しました
- 固定接続の回復性と接続プールが有効な場合、サーバーを削除するセッションの原因とは、セッション復旧試行中に SQL Server に不適切な状態を送信

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversion-mdmd"></a>バグ修正、 [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- バグを修正しましたが、Kerberos 認証を使用して一括挿入は、「アクセス拒否」エラーで失敗でした
- UnixODBC 2.3.1 の下のバージョンに存在するバグの回避策を削除しました (ドライバーには、unixODBC に渡される特定のバッファーのサイズが 2 倍に)
- 接続の回復性を修正しました (再接続) ColumnEncryption を使用するときにハング = 有効になっています。
- 場所と「Active Directory 対話型認証」を使用してオプション Azure Authentication DSN の作成のバグを修正ウィンドウは応答しない (Windows) を受ける可能性があります。
- (接続ハンドルを消去するときに発生した) 非同期実行が有効な場合は、ODBC のシャット ダウン中にまれなクラッシュを修正しました
- SQL ドライバーが時間の長いストアド プロシージャの実行中に CPU 使用量が多い原因となった問題を修正しました
- 固定できない変換せずに暗号化された varbinary (max) 列にデータを取得するには
- Null に varchar (max) の後に暗号化された列を使用してフェッチ SQLGetData() 静的カーソルで問題を修正、次の列も null データがある場合でも
- Always Encrypted で varbinary (max) フィールドのフェッチに問題を修正しました
- Always Encrypted を使用していない setlocale() の問題を修正しました
- SQLDescribeParam() で Always Encrypted で XML 型のストアド プロシージャのパラメーターで呼び出されたときにエラーを返す問題を修正しました
- SQLTables で作業していないエスケープ後のアンダー スコアを修正しました
- ヘブライ語のデータ (varchar) が Linux 上のワイド文字として返された場合に切り捨てられますバグを修正しました
- Shift JIS エンコードされた char と varchar utf-8 アプリケーションからのクエリに関する問題を修正しました
- Macos を Linux スタイルのファイル名に返さ SQL_DRIVER_NAME パラメーターを持つ SQLGetInfo を呼び出すことで、バグを修正しました
- 入力を使用して、Windows 1252 文字データの読み込みファイル 32 k のエラーが発生、BCP ユーティリティを使用して、VARCHAR 列にバイトを超える問題を修正しました
