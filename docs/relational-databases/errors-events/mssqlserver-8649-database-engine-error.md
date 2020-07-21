---
title: MSSQLSERVER_8649 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d305866fb884b62540cfbe2cc13a613981999749
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765283"
---
# <a name="mssqlserver_8649"></a>MSSQLSERVER_8649
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|8649|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|COST_TOO_HIGH|  
|メッセージ テキスト|このクエリの見積コスト (%d) が設定されたしきい値 %d を超えたので、クエリは取り消されました。 システム管理者に連絡してください。|  
  
## <a name="explanation"></a>説明  
このクエリの見積コストは、QUERY_GOVERNOR_COST_LIMIT に対して設定されているしきい値を超えたので、クエリが取り消されました。  
  
## <a name="user-action"></a>ユーザーの操作  
QUERY_GOVERNOR_COST_LIMIT オプションの設定値を大きくします。  
  
## <a name="see-also"></a>参照  
[SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](~/t-sql/statements/set-query-governor-cost-limit-transact-sql.md)  
  
