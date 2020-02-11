---
title: Oracle への接続 (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 23a48cb6-ff30-49bb-b4a7-603ebcab336f
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 42ab1e77dbdb7cee237a9ec22c49a725a64390c0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68264480"
---
# <a name="connect-to-oracle-oracletosql"></a>Oracle への接続 (OracleToSQL)
[ **Oracle への接続**] ダイアログボックスを使用すると、移行する oracle データベースに接続できます。  
  
このダイアログボックスにアクセスするには、[**ファイル**] メニューの [ **Oracle への接続**] をクリックします。 以前に接続している場合は、コマンドが**Oracle に再接続**されます。  
  
## <a name="options"></a>オプション  
**プロバイダー**  
Oracle データベースへの接続に使用するデータアクセスプロバイダーを選択します。 使用可能なプロバイダーは、Oracle クライアントプロバイダーと OLE DB プロバイダーです。 既定値は [Oracle Client Provider (Oracle クライアントプロバイダー) です。  
  
**モード**  
[標準]、[TNSNAME]、[接続文字列モード] のいずれかを選択します。  
  
-   標準モードでは、プロバイダー、サーバー名、サーバーポート、Oracle SID、ユーザー名、およびパスワードの値を入力または選択します。  
  
-   TNSNAME モードでは、Oracle データベース、ユーザー名、およびパスワードの接続識別子 (TNS alias) を入力します。  
  
-   接続文字列モードでは、接続文字列を指定します。  
  
    > [!IMPORTANT]  
    > 接続文字列モードを使用することはお勧めしません。これは、テキストにパスワードが含まれる可能性があり、クリアテキストとして送信されるためです。  
  
既定値は [標準モードです。  
  
**サーバー名**  
Oracle サーバー名を入力します。 既定のサーバー名は、コンピューター名と同じです。 これは標準モードオプションです。  
  
**サーバーポート**  
Oracle への接続に 1521 (既定値) 以外のポート番号を使用している場合は、ポート番号を入力します。 これは標準モードオプションです。  
  
**接続識別子**  
Oracle 接続識別子を入力します。 これは、ローカル tnsnames. ora ファイルで定義されているデータベースの別名です。  
  
これは TNSNAME モードオプションです。  
  
**Oracle SID**  
データベースの SID を入力します。 SID は、コンピューター上の Oracle データベースを区別するための識別子です。 データベースの既定の SID は、データベース名の最初の8文字です。  
  
これは標準モードオプションです。  
  
**ユーザー名**  
SSMA が Oracle データベースへの接続に使用するユーザー名を入力します。  
  
**パスワード**  
入力されたユーザー名のパスワードを入力します。  
  
**接続文字列**  
> [!IMPORTANT]  
> 接続文字列モードを使用することはお勧めしません。これは、テキストにパスワードが含まれる可能性があり、クリアテキストとして送信されるためです。  
  
接続文字列モードを使用する場合は、Oracle への接続に使用する完全な接続文字列を入力します。  
  
接続文字列は、パラメーターの名前と値のペアで構成されます。  
  
-   OLE DB の接続文字列情報については、MSDN ライブラリの「 [Microsoft OLE DB Provider for Oracle](https://go.microsoft.com/fwlink/?LinkId=85640) 」を参照してください。  
  
SSMA 接続文字列の場合は、常に Provider パラメーターを含めます。 また、Oracle に接続するときは、Port パラメーターを必ず含めてください。  
  
