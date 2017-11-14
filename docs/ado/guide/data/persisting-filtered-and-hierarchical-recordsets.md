---
title: "永続化するフィルター選択された階層レコード セットは、|Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filtered Recordset persistence [ADO]
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: d01aeb4d-4e43-450b-b3f2-0c27eaaf9f86
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8de12620e57fe9cf7235c2a1f5a1442b429197d0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>レコード セットは、フィルター選択された階層を保持します。
場合、[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティは、有効で、 **Recordset**フィルターでアクセス可能な行のみが保存されます。 場合、**レコード セット**は階層構造、現在の子**レコード セット**とその子を保存する親を含む**レコード セット**です。 場合、**保存**メソッドが子**レコード セット**が呼び出されると、子とその子をすべて保存されますが、親はありません。 階層の詳細については**レコード セット**を参照してください[データ シェイプ](../../../ado/guide/data/data-shaping.md)です。  
  
> [!NOTE]
>  階層を保存するときにいくつかの制限が適用**レコード セット**(データ図形) XML 形式でします。 詳細については、次を参照してください。 [XML 形式で保持するレコード](../../../ado/guide/data/persisting-records-in-xml-format.md)です。

