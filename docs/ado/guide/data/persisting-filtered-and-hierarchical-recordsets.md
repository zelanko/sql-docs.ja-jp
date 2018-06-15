---
title: 永続化するフィルター選択された階層レコード セットは、|Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
manager: craigg
ms.openlocfilehash: da1d0d1538d86738e576b01aa176ffde206a9cdb
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272191"
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>レコード セットは、フィルター選択された階層を保持します。
場合、[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティは、有効で、 **Recordset**フィルターでアクセス可能な行のみが保存されます。 場合、**レコード セット**は階層構造、現在の子**レコード セット**とその子を保存する親を含む**レコード セット**です。 場合、**保存**メソッドが子**レコード セット**が呼び出されると、子とその子をすべて保存されますが、親はありません。 階層の詳細については**レコード セット**を参照してください[データ シェイプ](../../../ado/guide/data/data-shaping.md)です。  
  
> [!NOTE]
>  階層を保存するときにいくつかの制限が適用**レコード セット**(データ図形) XML 形式でします。 詳細については、次を参照してください。 [XML 形式で保持するレコード](../../../ado/guide/data/persisting-records-in-xml-format.md)です。
