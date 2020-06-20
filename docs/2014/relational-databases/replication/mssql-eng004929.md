---
title: MSSQL_ENG004929 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG004929 error
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b202b28eabe1feb1ed180bda0d58d2e84c7d10d4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049272"
---
# <a name="mssql_eng004929"></a>MSSQL_ENG004929
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|4929|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|%S_MSG '%.*ls' は、レプリケーションでパブリッシュされているので変更できません。|  
  
## <a name="explanation"></a>説明  
 通常、このエラーは、トランザクション レプリケーションでパブリッシュされているテーブル上の主キーの制約を削除しようとすると発生します。 トランザクション レプリケーションではパブリッシュされたテーブルごとに 1 つの主キーが必要であるため、制約は削除できません。  
  
## <a name="user-action"></a>ユーザーの操作  
 制約を削除するには、最初にテーブルに関連付けられているアーティクルを削除します。 詳細については、「[Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md)」 (既存のパブリケーションでのアーティクルの追加および削除) を参照してください。 レプリケートされていないデータベースでこのエラーが発生した場合は、[sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) を実行して、データベース内のオブジェクトにレプリケート済みのマークが付かないようにしてください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md)  
  
  
