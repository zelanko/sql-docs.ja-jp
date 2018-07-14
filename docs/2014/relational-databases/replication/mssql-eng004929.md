---
title: MSSQL_ENG004929 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG004929 error
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b3d66948ad92e18fed77002f956cac9af07c04b7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37186099"
---
# <a name="mssqleng004929"></a>MSSQL_ENG004929
    
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
 制約を削除するには、最初にテーブルに関連付けられているアーティクルを削除します。 詳細については、「[既存のパブリケーションでのアーティクルの追加および削除](publish/add-articles-to-and-drop-articles-from-existing-publications.md)」を参照してください。 レプリケートされていないデータベースでこのエラーが発生した場合は、[sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) を実行して、データベース内のオブジェクトにレプリケート済みのマークが付かないようにしてください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md)  
  
  
