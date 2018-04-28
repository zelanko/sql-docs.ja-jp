---
title: 修正されたバグのリスト |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- driver
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
caps.latest.revision: 69
author: v-makouz
ms.author: genemi
manager: kenvh
ms.workload: Active
ms.openlocfilehash: 58da69ed6c4b7b046f8d1bc1ddf4e23b71b99a29
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="list-of-bugs-fixed"></a>修正されたバグの一覧

このページには、以降で、各リリースで修正されたバグの一覧が含まれています[!INCLUDE[msCoName](../../includes/msconame_md.md)]の ODBC ドライバーの 17。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversionmdmd"></a>バグの修正、[!INCLUDE[msCoName](../../includes/msconame_md.md)]の ODBC ドライバー 17.1 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]

- SQLFreeHandle MARS を有効にし、接続属性を呼び出すときに、1 秒の遅延を固定"Encrypt = [はい]"
- SQLGetData で渡されたバッファーのサイズが小さいときに取得されるデータ (Windows) に、エラー 22003 クラッシュを修正
- 切り捨てられた ADAL エラー メッセージを修正
- 整数を小数点の数を浮動小数点に変換するときに、32 ビット Windows でまれなバグを修正
- ここで、データの切り捨てエラーを返す二重で Always Encrypted で 10 進数のフィールドへの挿入は問題を修正しました
- MacOS インストーラーに、警告を修正
- 固定接続の回復との接続プール両方が有効な場合、サーバーから削除するセッションの原因は、セッション復旧試行中に SQL Server に無効な状態を送信

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversionmdmd"></a>バグの修正、[!INCLUDE[msCoName](../../includes/msconame_md.md)]の ODBC ドライバーの 17 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]

- バグを修正、Kerberos 認証を使用して、一括挿入でした「アクセスが拒否されました」エラーで失敗します。
- UnixODBC 2.3.1 以降のバージョンに存在バグの回避策を削除 (ドライバーには、unixODBC に渡される特定のバッファーのサイズが 2 倍に)
- 接続の回復を固定 ColumnEncryption を使用するときにハング (再接続) = 有効になっています。
- 場所と「Active Directory の対話型認証」を使用してオプション Azure 認証 DSN の作成のバグを修正ウィンドウ状態になる応答しない状態 (Windows)
- (接続ハンドルをクリアするときに発生した)、非同期実行が有効にすると、ODBC のシャット ダウン中にまれなクラッシュを修正
- SQL ドライバーが CPU の消費時間ストアド プロシージャの実行中に原因となった問題を修正しました
- 固定できない変換せずに暗号化された varbinary (max) 列にデータを取得するには
- ここで null varchar (max) の後に暗号化された列を使用してフェッチ SQLGetData() は静的カーソルで問題を修正、次の列も null データがある場合でも
- Always Encrypted で varbinary (max) フィールドを取得して問題を修正しました。
- Always Encrypted を使用して setlocale() の問題の修正
- SQLDescribeParam() で Always Encrypted で XML 型のストアド プロシージャのパラメーターで呼び出されたときにエラーを返すことで問題を修正しました。
- SQLTables で作業していないエスケープされたアンダー スコアの固定
- バグの修正、ヘブライ語データ (varchar) が Linux でのワイド文字として返された場合に切り捨てられます
- SHIFT-JIS でエンコードされた char と varchar utf-8 アプリケーションからのクエリを実行すると問題を修正しました。
- SQL_DRIVER_NAME パラメーターで SQLGetInfo を呼び出して返される位置 Linux スタイル filename macos バグを修正
- 入力を使用して、Windows 1252 文字データの読み込みファイル BCP ユーティリティを使用して VARCHAR 列にバイトがエラーになる 32 k を超える問題を修正しました
