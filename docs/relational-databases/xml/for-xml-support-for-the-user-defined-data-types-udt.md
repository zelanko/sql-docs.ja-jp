---
title: ユーザー定義データ型 (UDT) の FOR XML サポート | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2416bdc2b49a88b4306ae46973eab70fc38c0d9d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67943267"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a>ユーザー定義データ型 (UDT) の FOR XML サポート
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  FOR XML は、共通言語ランタイム (CLR) のユーザー定義データ型 (UDT) をサポートしていません。  
  
 CLR のユーザー定義データ型で FOR XML を使用するには、そのデータ型で XML シリアル化を指定して、FOR XML SELECT 句で XML への明示的なキャストを使用します。  
  
## <a name="see-also"></a>参照  
 [各種 SQL Server データ型の FOR XML サポート](../../relational-databases/xml/for-xml-support-for-various-sql-server-data-types.md)  
  
  
