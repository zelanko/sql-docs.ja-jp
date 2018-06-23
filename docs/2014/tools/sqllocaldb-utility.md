---
title: SqlLocalDB ユーティリティ |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SqlLocalDB utility [SQL Server]
- local database runtime utility
- LocalDB, SqlLocalDB Utility
ms.assetid: d785cdb7-1ea0-4871-bde9-1ae7881190f5
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 368c770520725aa83ccb4852881e4d62d487998d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083323"
---
# <a name="sqllocaldb-utility"></a>SqlLocalDB ユーティリティ
  使用して、`SqlLocalDB`のインスタンスを作成するユーティリティ[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssExpCurrent](../includes/ssexpcurrent-md.md)] **LocalDB**です。 `SqlLocalDB`ユーティリティ (SqlLocalDB.exe) はユーザーおよび開発者が作成およびのインスタンスを管理するシンプルなコマンド ライン ツール[!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB**です。 使用する方法については**LocalDB**を参照してください[SQL Server 2014 Express LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
SqlLocalDB.exe   
{  
      [ create   | c ] <instance-name><instance-version> [-s ]  
    | [ delete   | d ] <instance-name>  
    | [ start    | s ] <instance-name>  
    | [ stop     | p ] <instance-name>  [ -i ] [ -k ]  
    | [ share    | h ] ["<user_SID>" | "<user_account>" ] "<private-name>""<shared-name>"  
    | [ unshare  | u ] "<shared-name>"  
    | [ info     | i ] <instance-name>  
    | [ versions | v ]  
    | [ trace    | t ] [ on | off ]  
    | [ help     | -? ]  
}  
```  
  
## <a name="arguments"></a>引数  
 [ **create** | **c** ] *\<instance-name>* *\<instance-version>* **[-s]**  
 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB** の新しいインスタンスを作成します。 `SqlLocalDB` バージョンを使用して[!INCLUDE[ssExpress](../includes/ssexpress-md.md)]で指定されたバイナリ*\<インスタンスのバージョン >* 引数。 バージョン番号は、1 桁以上の 10 進数の数値書式で指定します。 マイナー バージョン番号 (サービス パック) は省略可能です。 たとえば、11.0 と 11.0.1186 という 2 つのバージョン番号のどちらも使用できます。 指定したバージョンがコンピューターにインストールされている必要があります。 バージョンにバージョン番号の既定値が指定されていない場合、`SqlLocalDB`ユーティリティです。 **–s** を追加した場合、 **LocalDB**の新しいインスタンスが起動します。  
  
 [ **share** | **h** ]  
 指定された共有名を使用して、 **LocalDB** の指定されたプライベート インスタンスを共有します。 ユーザー SID またはアカウント名を省略した場合、既定で現在のユーザーになります。  
  
 [ **unshared** | **u** ]  
 **LocalDB**の指定した共有インスタンスの共有を停止します。  
  
 [ **delete** | **d** ] *\<instance-name>*  
 指定した [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB** のインスタンスを削除します。  
  
 [ **start** | **s** ] "*\<instance-name>*"  
 指定した [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB** のインスタンスを起動します。 成功した場合、ステートメントから **LocalDB**の名前付きパイプ アドレスが返されます。  
  
 [ **stop** | **p** ] *\<instance-name>* **[-i]** **[-k]**  
 指定した [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB** のインスタンスを停止します。 追加 **– i**でインスタンスのシャット ダウンを要求、`NOWAIT`オプション。 **–k** を追加した場合は、インスタンス プロセスに通知することなく、そのプロセスを停止します。  
  
 [ **info** | **i** ] [ *\<instance-name>* ]  
 現在のユーザーが所有する [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB** のすべてのインスタンスを一覧表示します。  
  
 *\<instance-name>* を指定すると、[!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** の指定したインスタンスの名前、バージョン、状態 (Running または Stopped)、および最後の起動時刻に加え、**LocalDB** のローカル パイプ名が返されます。  
  
 [ **trace** | **t** ] **on** | **off**  
 **トレース**のトレースを有効に、`SqlLocalDB`現在のユーザーの API を呼び出します。 **trace off** はトレースを無効にします。  
  
 **-?**  
 返します。 それぞれの説明を簡単な`SqlLocalDB`オプション。  
  
## <a name="remarks"></a>コメント  
 引数 *instance name* は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 識別子のルールに従っているか、二重引用符で囲む必要があります。  
  
 引数を指定せずに SqlLocalDB を実行すると、ヘルプ テキストが返されます。  
  
 start 以外の操作は、現在ログインしているユーザーに属するインスタンスでのみ実行できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-an-instance-of-localdb"></a>A. LocalDB のインスタンスを作成する  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] バイナリを使用して `DEPARTMENT` という名前の [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB** のインスタンスを作成し、そのインスタンスを起動する例を次に示します。  
  
```  
SqlLocalDB.exe create "DEPARTMENT" 12.0 -s  
```  
  
### <a name="b-working-with-a-shared-instance-of-localdb"></a>B. LocalDB の共有インスタンスを操作する  
 管理者権限を使用してコマンド プロンプトを開きます。  
  
```  
SqlLocalDB.exe create "DeptLocalDB"  
SqlLocalDB.exe share "DeptLocalDB" "DeptSharedLocalDB"  
SqlLocalDB.exe start "DeptLocalDB"  
SqlLocalDB.exe info "DeptLocalDB"  
REM The previous statement outputs the Instance pipe name for the next step  
sqlcmd –S np:\\.\pipe\LOCALDB#<use your pipe name>\tsql\query  
CREATE LOGIN NewLogin WITH PASSWORD = 'Passw0rd!!@52';   
GO  
CREATE USER NewLogin;  
GO  
EXIT  
```  
  
 次のコードを実行して、 **ログインを使用して、** LocalDB `NewLogin` の共有インスタンスに接続します。  
  
```  
sqlcmd –S (localdb)\.\DeptSharedLocalDB -U NewLogin -P Passw0rd!!@52  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 Express LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
  