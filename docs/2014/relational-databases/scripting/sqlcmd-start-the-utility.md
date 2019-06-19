---
title: sqlcmd ユーティリティの起動 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec1ec91705dfb9194f42c079cb7b3d5100c9d396
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66090106"
---
# <a name="start-the-sqlcmd-utility"></a>sqlcmd ユーティリティの起動
  `sqlcmd` を使用するには、最初にユーティリティを起動し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続する必要があります。 既定のインスタンスまたは名前付きインスタンスのいずれにも接続できます。 最初の手順として、`sqlcmd` ユーティリティを起動します。  
  
> [!NOTE]  
>  `sqlcmd` の既定の認証は Windows 認証です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用するには、 **-U** オプションと **-P** オプションを追加して、ユーザー名とパスワードを指定する必要があります。  
  
> [!NOTE]  
>  既定では、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] は名前付きインスタンスの **sqlexpress**としてインストールされます。  
  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のこのインスタンスに接続したことがない場合、接続を受け入れるには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の構成が必要になることがあります。  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-default-instance-of-sql-server"></a>sqlcmd ユーティリティを起動し、SQL Server の既定のインスタンスに接続するには  
  
1.  **[スタート]** ボタンをクリックし、 **[ファイル名を指定して実行]** をクリックします。 **[名前]** ボックスに「 **cmd**」と入力して、 **[OK]** をクリックします。コマンド プロンプト ウィンドウが開きます  
  
2.  コマンド プロンプトで、「`sqlcmd`」と入力します。  
  
3.  Enter キーを押します。  
  
     これで、コンピューターで実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスに、信頼できる接続を確立しました。  
  
     **1 >** は、`sqlcmd`プロンプト行の数を指定します。 Enter キーを押すたびに、この番号が 1 ずつ増えます。  
  
4.  終了、`sqlcmd`セッションで、「`EXIT`で、`sqlcmd`プロンプト。  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-named-instance-of-sql-server"></a>sqlcmd ユーティリティを起動し、SQL サーバーの名前付きインスタンスに接続するには  
  
1.  コマンド プロンプトを開く ウィンドウ、および種類`sqlcmd -S` *myserver \instancename*します。 *myServer\instanceName* には、コンピューターの実際の名前と、接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを指定してください。  
  
2.  Enter キーを押します。  
  
     `sqlcmd`プロンプト (1 >) の指定されたインスタンスに接続されていることを示します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
    > [!NOTE]  
    >  入力した [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントはバッファーに格納されます。 GO コマンドが見つかると、ステートメントがバッチとして実行されます。  
  
## <a name="see-also"></a>関連項目  
 [sqlcmd を使用した Transact-SQL スクリプト ファイルの実行](sqlcmd-run-transact-sql-script-files.md)  
  
  
