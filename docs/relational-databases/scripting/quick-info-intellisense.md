---
title: "クイック ヒント (IntelliSense) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Quick Info option [IntelliSense]
- declarations [IntelliSense]
- IntelliSense [SQL Server], Quick Info
- identifier declarations [IntelliSense]
ms.assetid: 3c8b59f4-1922-4bde-844f-5f2306514d96
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0fe3ba8344fafc7523b4e46a4557bcaf35c11ced
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="quick-info-intellisense"></a>クイック ヒント (IntelliSense)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense の**クイック ヒント** オプションには、コード内の識別子に関する完全な宣言が表示されます。 識別子の上にマウスのポインターを置くと、黄色のポップアップ ウィンドウにその宣言が表示されます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、データベース エンジン クエリ エディターおよび XML クエリ エディターで **クイック ヒント** を利用できます。  
  
## <a name="transact-sql-quick-info"></a>Transact-SQL クイック ヒント  
 **クイック ヒント** には、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターに 2 種類の情報が表示されます。 デバッグ モードでない場合、 **クイック ヒント** には式の宣言が表示されます。 デバッグ モードの場合は、式の名前とその現在の値が **クイック ヒント** に表示されます。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターでは、 **クイック ヒント** は、IntelliSense によってサポートされる [!INCLUDE[tsql](../../includes/tsql-md.md)] 構文の部品でのみ利用できます。 たとえば、IntelliSense によってサポートされないデータ型を持つオブジェクトの識別子上にマウス ポインターを移動すると、そのデータ型はサポートされていない旨のメッセージが **クイック ヒント** のポップアップ ウィンドウに表示されます。  
  
## <a name="see-also"></a>参照  
 [IntelliSense でサポートされている Transact-SQL 構文](../../relational-databases/scripting/transact-sql-syntax-supported-by-intellisense.md)  
  
  
