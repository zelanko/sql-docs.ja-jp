---
description: フィルター処理されたレコードセットおよび階層レコードセットの保持
title: フィルター処理された階層化されたレコードセットの保持 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- filtered Recordset persistence [ADO]
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: d01aeb4d-4e43-450b-b3f2-0c27eaaf9f86
author: rothja
ms.author: jroth
ms.openlocfilehash: a69b491f4bb5834331b9cfa582b6f72d248ba317
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453064"
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>フィルター処理されたレコードセットおよび階層レコードセットの保持
[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティが**レコードセット**に対して有効になっている場合は、フィルターでアクセスできる行だけが保存されます。 **レコードセット**が階層化されている場合、現在の子**レコードセット**とその子が保存されます (親**レコード**セットを含む)。 子**レコードセット**の**Save**メソッドが呼び出されると、子とそのすべての子が保存されますが、親は保存されません。 階層 **レコードセット**の詳細については、「 [データシェイプ](../../../ado/guide/data/data-shaping.md)」を参照してください。  
  
> [!NOTE]
>  階層的な **レコードセット** (データ図形) を XML 形式で保存する場合には、いくつかの制限が適用されます。 詳細については、「 [XML 形式でのレコードの永続](../../../ado/guide/data/persisting-records-in-xml-format.md)化」を参照してください。
