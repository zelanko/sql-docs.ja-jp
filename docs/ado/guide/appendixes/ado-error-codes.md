---
description: ADO エラーコードのキャプチャ
title: ADO エラーコード |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO], error codes
ms.assetid: 3aee61c7-a9b7-4596-b78e-5828a00d0281
author: rothja
ms.author: jroth
ms.openlocfilehash: b5c3f5f00355bb2c9f9762db1d317a592b4df7dc
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/25/2020
ms.locfileid: "88805334"
---
# <a name="capture-ado-error-codes"></a>ADO エラーコードのキャプチャ
ADO 自体は、 [errors](../../reference/ado-api/errors-collection-ado.md)コレクションの[Error](../../reference/ado-api/error-object.md)オブジェクトで返されるプロバイダーエラーに加えて、実行時環境の例外処理機構にエラーを返すことができます。 ADO エラーをキャプチャするには、Microsoft® Visual Basic の **On error** ステートメントや Microsoft Visual C++®の **try-catch** ブロックなどのプログラミング言語を使用します。

 ADO エラーコードの一覧については、「 [Errorvalueenum](../../reference/ado-api/errorvalueenum.md)」を参照してください。

## <a name="see-also"></a>参照
 [エラーオブジェクト](../../reference/ado-api/error-object.md)[エラーの収集 (ADO)](../../reference/ado-api/errors-collection-ado.md)