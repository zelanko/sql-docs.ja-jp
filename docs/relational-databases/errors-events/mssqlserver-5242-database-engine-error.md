---
title: MSSQLSERVER_5242 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5242 (Database Engine error)
ms.assetid: 712b1a10-2f87-41df-a111-1ed9f14102d4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cad6c107e6ca130ef19908f71e356a929589e1cd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47631010"
---
# <a name="mssqlserver5242"></a>MSSQLSERVER_5242
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|5242|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名||  
|メッセージ テキスト|データベース '%.*ls'(ID:%d) のページ %S_PGID で内部操作中に、一貫性が損なわれていることが検出されました。 テクニカル サポートにお問い合わせください。 参照番号 %ld。|  
  
## <a name="explanation"></a>説明  
エラー メッセージで参照されているデータベース ページで構造の一貫性が損なわれています。  
  
## <a name="see-also"></a>参照  
[DBCC CHECKDB &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
[データベース ファイルとファイル グループ](~/relational-databases/databases/database-files-and-filegroups.md)  
  
