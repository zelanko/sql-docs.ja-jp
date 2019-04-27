---
title: ADD TARGET 引数の構成可能なパラメーターの取得 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], ADD TARGET argument
- xe
ms.assetid: 08454543-c5c8-4ca3-9af9-f1d82264471c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 368f019453fe0c8f5fcbef245db3f4b50769a210
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779147"
---
# <a name="get-the-configurable-parameters-for-the-add-target-argument"></a>ADD TARGET 引数の構成可能パラメーターの取得
  この作業には、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のクエリ エディターを使用した次の手順の実行も含まれます。  
  
 この手順でステートメントの実行が完了すると、クエリ エディターの **[結果]** タブに次の列が表示されます。  
  
-   package_name  
  
-   target_name  
  
-   parameter_name  
  
-   parameter_type  
  
-   required  
  
##  <a name="BeforeYouBegin"></a> はじめに  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 拡張イベント セッションを作成する前に、CREATE EVENT SESSION または ALTER EVENT SESSION で ADD TARGET 引数を使用する際に設定できるパラメーターを確認すると役立つことがあります。  
  
### <a name="to-get-the-configurable-parameters-for-the-add-target-argument-using-query-editor"></a>クエリ エディターで ADD TARGET 引数の構成可能パラメーターを取得するには  
  
-   クエリ エディターで、次のステートメントを実行します。  
  
    ```  
    SELECT p.name package_name, o.name target_name, c.name parameter_name,   
    c.type_name parameter_type, CASE c.capabilities_desc WHEN 'mandatory' THEN 'yes' ELSE 'no' END   
    required   
    FROM sys.dm_xe_objects o JOIN sys.dm_xe_packages p ON o.package_guid = p.guid   
    JOIN sys.dm_xe_object_columns c ON o.name = c.object_name AND c.column_type = 'customizable'  
    WHERE o.object_type = 'target'   
    ORDER BY package_name, target_name, required DESC  
    ```  
  
## <a name="see-also"></a>関連項目  
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)   
 [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
