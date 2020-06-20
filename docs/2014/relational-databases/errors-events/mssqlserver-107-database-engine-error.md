---
title: MSSQLSERVER_107 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 107 (Database Engine error)
ms.assetid: f33f514c-56aa-42e2-841b-e91244da90e2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eca3dfce05d345506477641c4605a39f14eeaf89
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969762"
---
# <a name="mssqlserver_107"></a>MSSQLSERVER_107
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|107|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|P_NOCORRMATCH|  
|メッセージ テキスト|列プレフィックス '%.*ls' とクエリで使用されているテーブル名または別名が一致しません。|  
  
## <a name="explanation"></a>説明  
 クエリの選択リストに、不適切な列プレフィックスで修飾されたアスタリスク (*) が含まれています。 このエラーは、次のような状況で返される可能性があります。  
  
-   列プレフィックス '%.*ls' とクエリで使用されているテーブル名または別名が一致しない。 たとえば、次のステートメントでは、FROM 句で定義していない別名 (`T1`) を列プレフィックスとして使用しています。  
  
    ```  
    SELECT T1.* FROM dbo.ErrorLog;  
    ```  
  
-   FROM 句でテーブルの別名を指定しているときに、テーブル名を列プレフィックスとして指定している。 たとえば、次のステートメントでは、FROM 句でテーブルの別名 (`ErrorLog`) を定義しているにもかかわらず、テーブル名 `T1` を列プレフィックスとして使用しています。  
  
    ```  
    SELECT ErrorLog.* FROM dbo.ErrorLog AS T1;  
    ```  
  
     FROM 句でテーブルの別名を指定した場合、テーブルの列のプレフィックスとして使用できるのはその別名だけです。  
  
## <a name="user-action"></a>ユーザーの操作  
 列プレフィックスとクエリの FROM 句で指定したテーブル名または別名を一致させます。 たとえば、上記のステートメントは次のように修正できます。  
  
```  
SELECT T1.* FROM dbo.ErrorLog AS T1;  
```  
  
 or  
  
```  
SELECT ErrorLog.* FROM dbo.ErrorLog;  
```  
  
## <a name="see-also"></a>参照  
 [MSSQLSERVER_4104](mssqlserver-4104-database-engine-error.md)  
  
  
