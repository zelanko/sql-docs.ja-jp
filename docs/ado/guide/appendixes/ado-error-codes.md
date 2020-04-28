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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9efe0f39ce304501096d9dcc682a0ea5d5137ee7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926997"
---
# <a name="capture-ado-error-codes"></a>ADO エラーコードのキャプチャ
ADO 自体は、 [errors](../../../ado/reference/ado-api/errors-collection-ado.md)コレクションの[Error](../../../ado/reference/ado-api/error-object.md)オブジェクトで返されるプロバイダーエラーに加えて、実行時環境の例外処理機構にエラーを返すことができます。 ADO エラーをキャプチャするには、Microsoft® Visual Basic の**On error**ステートメントや Microsoft Visual C++®の**try-catch**ブロックなどのプログラミング言語を使用します。

 ADO エラーコードの一覧については、「 [Errorvalueenum](../../../ado/reference/ado-api/errorvalueenum.md)」を参照してください。

## <a name="see-also"></a>参照
 [エラーオブジェクト](../../../ado/reference/ado-api/error-object.md)[エラーの収集 (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)
