---
title: "Oracle (OracleToSQL) への接続 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23a48cb6-ff30-49bb-b4a7-603ebcab336f
caps.latest.revision: "5"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 6350438d06f574096f78c44af85a298b5003423a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="connect-to-oracle-oracletosql"></a>Oracle (OracleToSQL) への接続します。
使用して、 **Connect to Oracle**を移行する Oracle データベースに接続する ダイアログ ボックス。  
  
このダイアログ ボックスにアクセスする、**ファイル**メニューの  **Connect to Oracle**です。 以前接続した場合、コマンドは**Oracle への再接続**です。  
  
## <a name="options"></a>オプション  
**プロバイダー**  
Oracle データベースへの接続用のデータ アクセス プロバイダーを選択します。 使用可能なプロバイダーは、Oracle Client プロバイダーと OLE DB プロバイダーです。 既定値は、Oracle クライアント プロバイダーです。  
  
**モード**  
標準、TNSNAME、または接続文字列のいずれかのモードを選択します。  
  
-   標準モードでは、入力またはプロバイダー、サーバー名、サーバーのポート、Oracle SID、ユーザー名とパスワードの値を選択します。  
  
-   TNSNAME モードでは、Oracle データベース、ユーザー名とパスワードの接続識別子 (TNS 別名) を入力します。  
  
-   接続文字列のモードでは、接続文字列を指定します。  
  
    > [!IMPORTANT]  
    > テキストは、パスワードを含める場合があり、クリア テキストとして送信されるため、接続文字列のモードを使用することはお勧めしません。  
  
既定値は、標準モードです。  
  
**サーバー名**  
Oracle サーバー名を入力します。 既定のサーバー名は、コンピューター名と同じです。 標準モードのオプションです。  
  
**[サーバー ポート]**  
Oracle への接続を 1521 (既定値) 以外のポート番号を使用している場合は、ポート番号を入力します。 標準モードのオプションです。  
  
**識別子を接続します。**  
Oracle の入力の識別子を接続します。 これは、ローカル tnsnames.ora ファイルで定義されているデータベースのエイリアスです。  
  
TNSNAME モード オプションです。  
  
**Oracle SID**  
データベースの SID を入力します。 SID は、コンピューター上の Oracle データベースを区別する識別子です。 データベースの既定で SID は、データベース名の最初の 8 文字です。  
  
標準モードのオプションです。  
  
**ユーザー名**  
SSMA が Oracle データベースへの接続に使用するユーザー名を入力します。  
  
**Password**  
ユーザー名に対応するパスワードを入力します。  
  
**[接続文字列]**  
> [!IMPORTANT]  
> テキストは、パスワードを含める場合があり、クリア テキストとして送信されるため、接続文字列のモードを使用することはお勧めしません。  
  
接続文字列のモードを使用する場合は、Oracle への接続の完全な接続文字列を入力します。  
  
接続文字列は、パラメーターの名前と値のペアで構成されます。  
  
-   OLE DB 接続文字列については、次を参照してください。 [Microsoft OLE DB Provider for Oracle](http://go.microsoft.com/fwlink/?LinkId=85640) 、MSDN ライブラリの記事です。  
  
SSMA 接続文字列の場合に、プロバイダーのパラメーターを必ず含めます。 また、Oracle に接続するときに、ポート パラメーターを含めることを確認します。  
  
