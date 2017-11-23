---
title: "データベース (チュートリアル) を作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: t-sql
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: tutorial creating a database
ms.assetid: e1e2c83f-dfad-4bb8-aa7a-09d3f69517ae
caps.latest.revision: "12"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 55a63275dc9e7d130614b5dece07b7f74edd53ca
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lesson-1-1---creating-a-database"></a>レッスン 1-1-データベースを作成します。
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]などの多くは[!INCLUDE[tsql](../includes/tsql-md.md)]ステートメント、CREATE DATABASE ステートメントが必要なパラメーター: データベースの名前。 また、CREATE DATABASE には、データベース ファイルを配置するディスクの場所など、多くのオプションのパラメーターがあります。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] でオプション パラメーターを指定せずに CREATE DATABASE を実行すると、これらの多くのパラメーターでは既定の値が使用されます。 このチュートリアルでは、オプションの構文パラメーターをほとんど使用しません。  
  
### <a name="to-create-a-database"></a>データベースを作成するには  
  
1.  クエリ エディターのウィンドウで、次のコードを入力します。ただし実行しないでください。  
  
    ```  
    CREATE DATABASE TestData  
    GO  
    ```  
  
2.  ポインターを使用して `CREATE DATABASE`の語句を選択し、 **F1**キーを押します。 SQL Server オンライン ブックの CREATE DATABASE のトピックが開きます。 この方法を使用して、このチュートリアルで使用する CREATE DATABASE やその他のステートメントの全構文を見つけることができます。  
  
3.  クエリ エディターで、 **F5** キーを押してステートメントを実行し、 `TestData`という名前のデータベースを作成します。  
  
データベースを作成すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] によって **モデル** データベースのコピーが作成され、その名前がデータベース名に変更されます。 オプション パラメーターでデータベースに大きな初期サイズを指定しなければ、この操作は数秒で完了します。  
  
> [!NOTE]  
> GO キーワードは、複数のステートメントを単一のバッチで送信した場合に、ステートメントを区切ります。 GO は、バッチにステートメントが 1 つしか入っていない場合はオプションです。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[テーブルの作成 (チュートリアル)](../t-sql/lesson-1-2-creating-a-table.md)  
  
## <a name="see-also"></a>参照  
[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
  
  
