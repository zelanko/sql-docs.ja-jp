---
title: ユーザー定義データ型 (UDT) の FOR XML サポート | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: xml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ee20338ce4cbcd36346fa999c65bd69219a22327
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33013449"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a>ユーザー定義データ型 (UDT) の FOR XML サポート
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  FOR XML は、共通言語ランタイム (CLR) のユーザー定義データ型 (UDT) をサポートしていません。  
  
 CLR のユーザー定義データ型で FOR XML を使用するには、そのデータ型で XML シリアル化を指定して、FOR XML SELECT 句で XML への明示的なキャストを使用します。  
  
## <a name="see-also"></a>参照  
 [各種 SQL Server データ型の FOR XML サポート](../../relational-databases/xml/for-xml-support-for-various-sql-server-data-types.md)  
  
  
