---
title: 共有メモリ プロトコルを使用した有効な接続文字列の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], shared memory
- aliases [SQL Server], shared memory
ms.assetid: 5fff42e8-377f-4b40-b0c8-b02393f8a1af
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c157d0b8cee3ee3635275c8f1b3c49fc6faf5a0a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63253598"
---
# <a name="creating-a-valid-connection-string-using-shared-memory-protocol"></a>共有メモリ プロトコルを使用した有効な接続文字列の作成
  同じコンピューター [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上で実行されているクライアントからに接続する場合は、共有メモリプロトコルを使用します。 共有メモリには、構成可能なプロパティはありません。 共有メモリは常に最初に試行されるプロトコルであり、 **[クライアント プロトコルのプロパティ]** 一覧にある **[有効なプロトコル]** 一覧の最上位から移動することはできません。 共有プロトコルを無効にすることは可能です。これは、他のプロトコルのトラブルシューティングを行うときに便利です。  
  
 共有メモリ プロトコルを使用して別名を作成することはできませんが、共有メモリが有効になっている状態で [!INCLUDE[ssDE](../../includes/ssde-md.md)] に名前で接続すると、共有メモリ接続が作成されます。 共有メモリ接続文字列の形式は、 `lpc:<servername>[\instancename]`です。  
  
## <a name="connecting-to-the-local-server"></a>ローカル サーバーへの接続  
 クライアントと同じコンピューター上で実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続する場合は、サーバー名として " **(local)** " を使用することもできます。 このような指定はあいまいさを残すのでお勧めできませんが、対象のコンピューター上でクライアントを実行していることがわかっている場合には便利な機能です。 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がラップトップコンピューター上で実行され、プロジェクトデータを格納する、モバイル接続されていないユーザー向けのアプリケーションを作成する場合、 **(ローカル)** に接続している[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアントは常に、ラップトップで実行されているに接続します。 " **(local)** " の代わりに "**localhost**" またはピリオド ( **.**) を使用することもできます。  
  
## <a name="verifying-your-connection-protocol"></a>接続プロトコルの確認  
 以下のクエリは、現在の接続に使用しているプロトコルを返します。  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a>例:  
 共有メモリ プロトコルが有効になっている場合に、以下の名前を使用すると、共有メモリを使用してローカル コンピューターに接続します。  
  
 `<servername>`  
  
 `<servername>\<instancename>`  
  
 `(local)`  
  
 `localhost`  
  
 共有メモリ接続のための別名を作成することはできません。  
  
> [!NOTE]  
>  
  **[サーバー]** ボックスで IP アドレスを指定すると、TCP/IP 接続になります。  
  
## <a name="see-also"></a>参照  
 [TCP/IP を使用した有効な接続文字列の作成](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [名前付きパイプを使用した有効な接続文字列の作成](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)   
 [ネットワーク プロトコルの選択](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
