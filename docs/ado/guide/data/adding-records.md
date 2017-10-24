---
title: "レコードを追加する |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: H1Hack27Feb2017
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- editing data [ADO], AddNew method
- editing data [ADO], adding data
ms.assetid: dd34669e-6f06-403b-9241-1c85c82aecc2
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f2804e2662e15c993fb3c5de7e1278a623ffcd47
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="adding-records-to-a-recordset"></a>レコードをレコード セットに追加します。
使用して、 **AddNew**メソッドを作成し、既存の新しいレコードの初期化を**Recordset**です。 使用することができます、**サポート**メソッドを**CursorOptionEnum**の値**adAddNew**現在のレコードを追加できるかどうかを確認する**レコードセット**オブジェクト。

 呼び出した後、 **AddNew**メソッド、新しいレコードを現在のレコードになりを呼び出した後は、**更新**メソッドです。 場合、 **Recordset**オブジェクトはブックマークをサポートしていない、別のレコードに移動すると、新しいレコードにアクセスできません。 そのため、カーソルの種類に応じてする必要がありますを呼び出して、 **Requery**メソッドを新しいレコードにアクセスできるようにします。

 呼び出す場合**AddNew** ADO が呼び出し、現在のレコードを編集するときに、新しいレコードを追加するときに、**更新**を保存する方法を変更し、レコードを作成して、新しいです。

 このセクションでは、次のトピックを扱います。

-   [AddNew を使用してレコードを追加します。](../../../ado/guide/data/adding-records-using-addnew.md)

-   [複数のフィールドを追加します。](../../../ado/guide/data/adding-multiple-fields.md)

-   [編集モードの決定](../../../ado/guide/data/determining-edit-mode.md)

-   [イミディ エイト AddNew とバッチ モードを使用してください。](../../../ado/guide/data/using-addnew-in-immediate-and-batch-modes.md)

