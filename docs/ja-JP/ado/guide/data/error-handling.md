---
title: エラー処理 | Microsoft Docs
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- reporting errors [ADO]
- errors [ADO]
- ADO, error handling
ms.assetid: 4909e413-f3b0-4183-8ad3-67b1434df742
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d22a7f0b1472fd5f55535bf6ffb9295729a0087
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="error-handling"></a>エラー処理
ADO では、いくつかの方法を使用して、発生したエラーのアプリケーションに通知します。 このセクションでは、ADO およびアプリケーションに通知する方法を使用しているときに発生するエラーの種類について説明します。 最後にこれらのエラーを処理する方法に関する提案をします。  
  
## <a name="how-does-ado-report-errors"></a>ADO がエラーを報告する方法  
 ADO では、いくつかの方法でのエラーについて通知します。  
  
-   ADO エラーには、実行時エラーが生成されます。 ADO エラーと同じ方法を使用するなど、他の実行時エラーの処理、 **On Error** Visual Basic でのステートメント。  
  
-   プログラムは、OLE DB からエラーを受信できます。 OLE DB エラーには、同様に実行時エラーが生成されます。  
  
-   このエラーは、1 つまたは複数のデータ プロバイダーに固有でかどうか**エラー**オブジェクトに配置、**エラー**のコレクション、**接続**データへのアクセスに使用されたオブジェクトエラーが発生したときに保存します。  
  
-   イベントを発生させたプロセスには、エラーも生成される場合に、エラー情報が格納されます。、**エラー**オブジェクトとイベントにパラメーターとして渡されます。 参照してください[ADO イベントを処理](../../../ado/guide/data/handling-ado-events.md)イベントについての詳細。  
  
-   更新プログラムまたはその他の一括操作を処理するときに発生する問題をバッチ処理、**レコード セット**によって示すことができます、**ステータス**のプロパティ、 **Recordset**です。 スキーマの制約違反または十分なアクセス許可を指定して、によってなど**可能**値。  
  
-   特定の関連する発生する問題**フィールド**現在のレコードがにより指定も、**ステータス**の各プロパティ**フィールド**で、**フィールド**のコレクション、**レコード**または**Recordset**です。 たとえば、完了できませんでした。 更新または互換性のないデータ型を指定できますで**FieldStatusEnum**値。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ADO エラー](../../../ado/guide/data/ado-errors.md)  
  
-   [プロバイダー エラー](../../../ado/guide/data/provider-errors.md)  
  
-   [フィールドに関連するエラー情報](../../../ado/guide/data/field-related-error-information.md)  
  
-   [レコードセット関連のエラー情報](../../../ado/guide/data/recordset-related-error-information.md)  
  
-   [他の言語でエラーを処理する](../../../ado/guide/data/handling-errors-in-other-languages.md)  
  
-   [エラーの予測](../../../ado/guide/data/anticipating-errors.md)
