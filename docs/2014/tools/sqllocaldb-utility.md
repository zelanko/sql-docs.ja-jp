---
title: SqlLocalDB Utility |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- SqlLocalDB utility [SQL Server]
- local database runtime utility
- LocalDB, SqlLocalDB Utility
ms.assetid: d785cdb7-1ea0-4871-bde9-1ae7881190f5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 168a343c208c7b9d98f3f03a802e40488602a7d0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85007070"
---
# <a name="sqllocaldb-utility"></a>SqlLocalDB ユーティリティ
  `SqlLocalDB`LocalDB のインスタンスを作成するには、ユーティリティを使用し [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssExpCurrent](../includes/ssexpcurrent-md.md)] **LocalDB**ます。 `SqlLocalDB`ユーティリティ (SqlLocalDB.exe) は、ユーザーおよび開発者が LocalDB のインスタンスを作成および管理できるようにするための単純なコマンドラインツールです [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB**。 **Localdb**の使用方法の詳細については、「 [SQL Server 2014 Express localdb](../database-engine/configure-windows/sql-server-2016-express-localdb.md)」を参照してください。  
  
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
 [**作成**  | **c** ] *\<instance-name>* *\<instance-version>* [**-s** ]  
 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** の新しいインスタンスを作成します。 `SqlLocalDB`[!INCLUDE[ssExpress](../includes/ssexpress-md.md)]引数で指定されたバージョンのバイナリを使用し *\<instance-version>* ます。 バージョン番号は、1 桁以上の 10 進数の数値書式で指定します。 マイナー バージョン番号 (サービス パック) は省略可能です。 たとえば、次の 2 つのバージョン番号のどちらも使用できます。11.0 または 11.0.1186。 指定したバージョンがコンピューターにインストールされている必要があります。 指定しない場合、バージョン番号は既定でユーティリティのバージョンに `SqlLocalDB` なります。 **-s** を追加した場合、**LocalDB** の新しいインスタンスが起動します。  
  
 [ **share** | **h** ]  
 指定された共有名を使用して、 **LocalDB** の指定されたプライベート インスタンスを共有します。 ユーザー SID またはアカウント名を省略した場合、既定で現在のユーザーになります。  
  
 [ **unshared** | **u** ]  
 **LocalDB**の指定した共有インスタンスの共有を停止します。  
  
 [**削除**  | **d** ]*\<instance-name>*  
 指定した [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** のインスタンスを削除します。  
  
 [**開始**  | **s** ] " *\<instance-name>* "  
 指定した [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** のインスタンスを起動します。 成功した場合、ステートメントから **LocalDB**の名前付きパイプ アドレスが返されます。  
  
 [**停止**  | **p** ] *\<instance-name>* [**-i** ] [**-k** ]  
 指定した [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** のインスタンスを停止します。 **-I**を追加すると、オプションを使用してインスタンスのシャットダウンが要求され `NOWAIT` ます。 **-k** を追加した場合は、インスタンス プロセスに通知することなく、そのプロセスを停止します。  
  
 [**情報**  |  ]**i** ] [ *\<instance-name>* ]  
 現在のユーザーが所有する [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** のすべてのインスタンスを一覧表示します。  
  
 *\<instance-name>* 指定された localdb インスタンスの名前、バージョン、状態 (実行中または停止)、最後の開始時刻、 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB** **localdb**のローカルパイプ名を返します。  
  
 [ **trace** | **t** ] **on** | **off**  
 **trace on**は、現在の `SqlLocalDB` ユーザーに対する API 呼び出しのトレースを有効にします。 **trace off** はトレースを無効にします。  
  
 **-?**  
 各オプションの簡単な説明を返し `SqlLocalDB` ます。  
  
## <a name="remarks"></a>解説  
 引数 *instance name* は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 識別子のルールに従っているか、二重引用符で囲む必要があります。  
  
 引数を指定せずに SqlLocalDB を実行すると、ヘルプ テキストが返されます。  
  
 start 以外の操作は、現在ログインしているユーザーに属するインスタンスでのみ実行できます。  
  
## <a name="examples"></a>例  
  
### <a name="a-creating-an-instance-of-localdb"></a>A. LocalDB のインスタンスを作成する  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] バイナリを使用して `DEPARTMENT` という名前の [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** のインスタンスを作成し、そのインスタンスを起動する例を次に示します。  
  
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
sqlcmd -S np:\\.\pipe\LOCALDB#<use your pipe name>\tsql\query  
CREATE LOGIN NewLogin WITH PASSWORD = 'Passw0rd!!@52';   
GO  
CREATE USER NewLogin;  
GO  
EXIT  
```  
  
 次のコードを実行して、 **ログインを使用して、** LocalDB `NewLogin` の共有インスタンスに接続します。  
  
```  
sqlcmd -S (localdb)\.\DeptSharedLocalDB -U NewLogin -P Passw0rd!!@52  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 Express LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
  
