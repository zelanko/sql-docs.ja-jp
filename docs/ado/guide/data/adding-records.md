---
title: レコードを追加する |Microsoft ドキュメント
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
- AddNew method [ADO]
- ADO, editing data
- editing data [ADO], AddNew method
- editing data [ADO], adding data
ms.assetid: dd34669e-6f06-403b-9241-1c85c82aecc2
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a1d367e572a7839b6a5d54b1c6460716aa09160
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271061"
---
# <a name="adding-records-to-a-recordset"></a>レコードをレコード セットに追加します。
使用して、 **AddNew**メソッドを作成し、既存の新しいレコードの初期化を**Recordset**です。 使用することができます、**サポート**メソッドを**CursorOptionEnum**の値**adAddNew**現在のレコードを追加できるかどうかを確認する**レコードセット**オブジェクト。

 呼び出した後、 **AddNew**メソッド、新しいレコードを現在のレコードになりを呼び出した後は、**更新**メソッドです。 場合、 **Recordset**オブジェクトはブックマークをサポートしていない、別のレコードに移動すると、新しいレコードにアクセスできません。 そのため、カーソルの種類に応じてする必要がありますを呼び出して、 **Requery**メソッドを新しいレコードにアクセスできるようにします。

 呼び出す場合**AddNew** ADO が呼び出し、現在のレコードを編集するときに、新しいレコードを追加するときに、**更新**を保存する方法を変更し、レコードを作成して、新しいです。

 このセクションでは、次のトピックを扱います。

-   [AddNew を使用してレコードを追加する](../../../ado/guide/data/adding-records-using-addnew.md)

-   [複数のフィールドの追加](../../../ado/guide/data/adding-multiple-fields.md)

-   [編集モードの決定](../../../ado/guide/data/determining-edit-mode.md)

-   [イミディエイト モードとバッチ モードで AddNew を使用する](../../../ado/guide/data/using-addnew-in-immediate-and-batch-modes.md)
