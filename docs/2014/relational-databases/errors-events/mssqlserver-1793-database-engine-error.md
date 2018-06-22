---
title: MSSQLSERVER_1793 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 808db1d0-acc1-41d0-9287-8a5455001a02
caps.latest.revision: 6
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: d36a4c1235b8b6b9e25a5fd635a37fd6052ae524
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072340"
---
# <a name="mssqlserver1793"></a>MSSQLSERVER_1793
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|1793|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|FILESTREAM_BASEDATA_NEED_SAME_PARTITION|  
|メッセージ テキスト|パーティション構成が FILESTREAM データに指定されていないため、操作 (インデックス '%.*ls' の削除) を実行できません。|  
  
## <a name="explanation"></a>説明  
 このメッセージは、FILESTREAM データを含むテーブルで、クラスター化インデックスの削除を実行する場合に、基本データに **MOVE TO** 句を指定したにもかかわらず、FILESTREAM データに **FILESTREAM_ON** 句が指定されていないときに表示されます。  
  
## <a name="user-action"></a>ユーザーの操作  
 FILESTREAM データを含むテーブルで、クラスター化インデックスを削除する場合は、次のオプションのどちらかを使用します。  
  
-   基本データに **MOVE TO** 句、FILESTREAM データに **FILESTREAM_ON** 句の両方を指定します。  
  
-   基本データに **MOVE TO** 句、FILESTREAM データに **FILESTREAM_ON** 句の両方とも指定しません。  
  
 次の例は、基本データにパーティション構成が指定されているにもかかわらず、FILESTREAM データには指定されているので、失敗します。  
  
```tsql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY] )  
GO  
```  
  
 次の例は、基本データに **MOVE TO** 句、FILESTREAM データに **FILESTREAM_ON** 句の両方が指定されているので、成功します。  
  
```tsql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY], filestream_on 'default' )  
GO  
```  
  
 次の例は、基本データに **MOVE TO** 句、FILESTREAM データに **FILESTREAM_ON** 句の両方とも指定されていないので、成功します。  
  
```tsql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF )  
GO  
```  
  
  