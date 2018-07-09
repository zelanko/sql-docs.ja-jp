---
title: Oracle ソース データベースへの接続 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- oraDb
ms.assetid: 220cf555-0db2-443c-8f87-8e413f3ca731
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: aadbab5ab6164ca68488cb8bc6dc6ed8e55aed3c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37164879"
---
# <a name="connect-to-an-oracle-source-database"></a>Oracle ソース データベースへの接続
  [Oracle ソース] ページを使用すると、Oracle ソース データベースへの接続に必要な情報を提供できます。 CDC インスタンスによって、接続している Oracle データベースの再実行ログが読み取られます。  
  
 **[Oracle 接続文字列]**  
 使用している Oracle データベースがあるコンピューターへの Oracle 接続文字列を入力します。 接続文字列は、次のいずれかの方法で記述されます。  
  
 `host[:port][/service name]`  
  
 接続文字列で Oracle Net 接続記述子を指定することもできます (例: `(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp) (HOST=erp.contoso.com) (PORT=1521)) (CONNECT_DATA=(SERVICE_NAME=orcl)))`  
  
 ディレクトリ サーバーまたは tnsnames を使用している場合は、接続文字列を接続の名前にすることができます。  
  
 **[Oracle ログ マイニング認証]**  
 ログ マイニングを承認されている Oracle データベース ユーザーの資格情報を入力するには、次のいずれかを選択します。  
  
-   **[Windows 認証]**: 現在の Windows ドメイン資格情報を使用する場合に選択します。 このオプションは、Oracle データベースが Windows 認証と連動するように構成されている場合にのみ使用できます。  
  
-   **[Oracle 認証]**: このオプションを選択する場合、接続先の Oracle データベースのユーザーの **[ユーザー名]** と **[パスワード]** を入力する必要があります。  
  
> [!NOTE]  
>  ユーザーがログ マイニング ユーザーになるには、Oracle データベースで次の特権を付与される必要があります。  
>   
>  -   \<any-captured-table> に対する SELECT  
> -   SELECT ANY TRANSACTION  
> -   DBMS LOGMNR に対する EXECUTE  
> -   V$LOGMNR CONTENTS に対する SELECT  
> -   V$ARCHIVED LOG に対する SELECT  
> -   V$LOG に対する SELECT  
> -   V$LOGFILE に対する SELECT  
> -   V$DATABASE に対する SELECT  
> -   V$THREAD に対する SELECT  
> -   ALL INDEXES に対する SELECT  
> -   ALL OBJECTS に対する SELECT  
> -   DBA OBJECTS に対する SELECT  
> -   ALL TABLES に対する SELECT  
>   
>  これらの特権を V$xxx に付与できないときは、V_S$xxx に付与してください。  
  
 **[接続テスト]**  
 Oracle データベースがあるリモート コンピューターとの接続が確立されているかどうかを確認するには、 **[テスト接続]** をクリックします。 接続が正常に確立されたかどうかを通知するダイアログ ボックスが開きます。  
  
> [!IMPORTANT]  
>  CDC デザイナーが管理者として実行されていない場合は、既知の問題のために Oracle ソース データベースとの接続が失敗する場合があります。 接続が失敗した場合は、 **[管理者として実行]** オプションを使用して CDC デザイナーを終了して再起動します。  
  
 このページでの情報入力が終了したら、 **[次へ]** をクリックして「 [Select Oracle Tables and Columns](select-oracle-tables-and-columns.md)」に進みます。  
  
## <a name="see-also"></a>参照  
 [SQL Server 変更データベース インスタンスを作成する方法](how-to-create-the-sql-server-change-database-instance.md)   
 [インスタンスのプロパティの編集](edit-instance-properties.md)  
  
  
