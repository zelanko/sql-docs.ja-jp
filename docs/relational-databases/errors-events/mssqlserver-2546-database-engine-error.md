---
title: MSSQLSERVER_2546 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8f907032d62bbb0a20c34c1c9d14cac1242bcaf5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780276"
---
# <a name="mssqlserver_2546"></a>MSSQLSERVER_2546
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|2546|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_INDEX_MARKED_DISABLED|  
|メッセージ テキスト|テーブル 'OBJECT_NAME' のインデックス 'INDEX_NAME' は無効に設定されています。 オンラインにするには、インデックスを再構築してください。|  
  
## <a name="explanation"></a>説明  
指定されているインデックスは、オフラインまたは無効に設定されています。 そのため、このインデックスをチェックできません。  
  
## <a name="user-action"></a>ユーザーの操作  
ALTER INDEX を使用してインデックスを再構築します。  
  
## <a name="see-also"></a>参照  
[ALTER INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/alter-index-transact-sql.md)  
[インデックスの再編成と再構築](~/relational-databases/indexes/reorganize-and-rebuild-indexes.md)  
  
