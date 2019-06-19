---
title: エッジ制約を変更する | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- alter edge constraints
- edge constraints [SQL Server]
- CONNECTION constraints
- edge constraints [Azure SQL Database]
- graph edge constraints
- SQL Graph
ms.assetid: ''
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e5b6a471156f0b1371c727ce96aac72f4f812dac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62693307"
---
# <a name="modify-edge-constraints"></a>エッジ制約を変更する
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  [!INCLUDE[ssNoversion](../../includes/ssnoversion-md.md)] では、 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用してエッジ制約を変更できます。 エッジの制約句の順序を変更するか、または新しい句を追加して、エッジ テーブルのエッジ制約を変更できます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **エッジ制約を変更するには、次のものを使用します。**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 テーブルに対する ALTER 権限が必要です。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用
 Transact-SQL を使用してエッジ制約を変更するには、まず既存のエッジ制約を削除してから、新しい定義を使用して再作成する必要があります。 詳細については、「[エッジ制約を削除する](../../relational-databases/tables/delete-edge-constraint.md)」および「[エッジ制約を作成する](../../relational-databases/tables/create-edge-constraints.md)」を参照してください。    
 
