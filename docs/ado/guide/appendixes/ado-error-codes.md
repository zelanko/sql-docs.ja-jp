---
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
ms.openlocfilehash: bceca521ebbf79f3e25fc0585130bc6bc96f7244
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761650"
---
# <a name="capture-ado-error-codes"></a>ADO エラーコードのキャプチャ
ADO 自体は、 [errors](../../../ado/reference/ado-api/errors-collection-ado.md)コレクションの[Error](../../../ado/reference/ado-api/error-object.md)オブジェクトで返されるプロバイダーエラーに加えて、実行時環境の例外処理機構にエラーを返すことができます。 ADO エラーをキャプチャするには、Microsoft® Visual Basic の**On error**ステートメントや Microsoft Visual C++®の**try-catch**ブロックなどのプログラミング言語を使用します。

 ADO エラーコードの一覧については、「 [Errorvalueenum](../../../ado/reference/ado-api/errorvalueenum.md)」を参照してください。

## <a name="see-also"></a>参照
 [エラーオブジェクト](../../../ado/reference/ado-api/error-object.md)[エラーの収集 (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)
