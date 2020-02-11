---
title: 名前付きパイプを使用した有効な接続文字列の作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], named pipes
- pipes [SQL Server]
- pipes [SQL Server], connecting to
- aliases [SQL Server], named pipes
- Named Pipes [SQL Server], connection strings
ms.assetid: 90930ff2-143b-4651-8ae3-297103600e4f
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 12d5cb30217a0580d4da101d614b4930cfd8184b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63065550"
---
# <a name="creating-a-valid-connection-string-using-named-pipes"></a>名前付きパイプを使用した有効な接続文字列の作成
  ユーザーが変更しない限り、の[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既定のインスタンスは名前付きパイププロトコルをリッスンするとき`\\.\pipe\sql\query`に、をパイプ名として使用します。 ここで、ピリオドはコンピューターがローカル コンピューターであることを示し、`pipe` は接続が名前付きパイプであることを示します。`sql\query` はパイプの名前を示します。 既定のパイプに接続するには、別名でもパイプ名に `\\<computer_name>\pipe\sql\query` を指定する必要があります。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が別のパイプで受信を待機する構成になっている場合は、パイプ名としてそのパイプを使用する必要があります。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がパイプとして `\\.\pipe\unit\app` を使用している場合、別名ではパイプ名として `\\<computer_name>\pipe\unit\app` を使用しなければなりません。  
  
 有効なパイプ名を作成するには、次の操作を行う必要があります。  
  
-   **[別名]** を指定します。  
  
-   **プロトコル**として [**名前付きパイプ**] を選択します。  
  
-   **パイプ名**を入力します。 または、[**パイプ名**] を空白[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のままにして、**プロトコル**と**サーバー**を指定した後に適切なパイプ名を入力 Configuration Manager ます。  
  
-   **サーバー**を指定してください。 名前付きのインスタンスの場合は、サーバー名とインスタンス名を指定できます。  
  
 Native Client コンポーネントは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、接続時に、指定されたエイリアス名のサーバー、プロトコル、パイプ名の値をレジストリから読み取り、または`np:\\<computer_name>\pipe\<pipename>` `np:\\<IPAddress>\pipe\<pipename>`の形式でパイプ名を作成します。名前付きインスタンスの場合、既定のパイプ名`\\<computer_name>\pipe\MSSQL$<instance_name>\sql\query`はです。  
  
> [!NOTE]  
>  既定[!INCLUDE[msCoName](../../includes/msconame-md.md)]では、Windows ファイアウォールはポート445を閉じます。 は[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ポート445を介して通信するため、が名前[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]付きパイプを使用して受信クライアント接続をリッスンするように構成されている場合は、ポートを再度開く必要があります。 ファイアウォールの構成方法については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「SQL Server アクセスのためのファイアウォール構成方法」か、またはファイアウォールについてのドキュメンテーションを参照してください。  
  
## <a name="connecting-to-the-local-server"></a>ローカル サーバーへの接続  
 クライアントと同じコンピューター上で実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続する場合は、サーバー名として `(local)` を使用することもできます。 
  `(local)` の使用はあいまいさを残すのでお勧めできませんが、対象のコンピューター上でクライアントを実行していることがわかっている場合には便利な機能です。 たとえば、営業スタッフは、ノート型コンピューター上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行し、プロジェクト データもそのノート型コンピューターに保存しておきます。このように、ネットワークに接続しないモバイル ユーザー用のアプリケーションの場合、(local) に接続するクライアントは、常にそのノート型コンピューターで実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続することになります。 
  `localhost` の代わりに、`(local)` またはピリオド (.) を使用することもできます。  
  
## <a name="verifying-your-connection-protocol"></a>接続プロトコルの確認  
 以下のクエリは、現在の接続に使用しているプロトコルを返します。  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a>例  
 既定のパイプに対するサーバー名による接続:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 既定のパイプに対する IP アドレスによる接続:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <leave blank>  
Protocol           Named Pipes  
Server             <IPAddress>  
  
```  
  
 既定以外のパイプに対するサーバー名による接続:  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\unit\app  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 名前付きのインスタンスに対するサーバー名による接続:  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\MSSQL$<instancename>\SQL\query  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 ローカル コンピューターに対する `localhost`による接続:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             localhost  
  
```  
  
 ローカル コンピューターに対するピリオドによる接続:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <left blank>  
Protocol           Named Pipes  
Server             .  
  
```  
  
> [!NOTE]  
>  ネットワークプロトコルを**sqlcmd**パラメーターとして指定する方法については、オンラインブックの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 「Sqlcmd を使用してデータベースエンジンに接続する方法」を参照してください。  
  
## <a name="see-also"></a>参照  
 [共有メモリ プロトコルを使用した有効な接続文字列の作成](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)   
 [TCP/IP を使用した有効な接続文字列の作成](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [ネットワーク プロトコルの選択](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
