---
title: "エラー処理 |Microsoft ドキュメント"
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
- reporting errors [ADO]
- errors [ADO]
- ADO, error handling
ms.assetid: 4909e413-f3b0-4183-8ad3-67b1434df742
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a1c85fb540f034c5a0a6870c38ea5797948d5fbd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

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
  
-   [レコード セットに関連するエラー情報](../../../ado/guide/data/recordset-related-error-information.md)  
  
-   [その他の言語でのエラーを処理](../../../ado/guide/data/handling-errors-in-other-languages.md)  
  
-   [エラーを予測します。](../../../ado/guide/data/anticipating-errors.md)

