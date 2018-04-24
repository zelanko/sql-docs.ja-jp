---
title: ErrorValueEnum |Microsoft ドキュメント
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
apitype: COM
f1_keywords:
- ErrorValueEnum
helpviewer_keywords:
- ErrorValueEnum enumeration [ADO]
ms.assetid: 9469ba3a-5e4f-4a10-bbb8-a51a6c9660ea
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a8a543a2e8816a23d420dd7bb007ae157d676f98
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="errorvalueenum"></a>ErrorValueEnum
ADO の実行時エラーの種類を指定します。  
  
 エラー番号の 3 つの形式の一覧が表示されます。  
  
-   正の 10 進数、10 進数形式で完全数の下位 2 バイトです。 この番号は、既定の Visual Basic エラー メッセージ ダイアログ ボックスに表示されます。 たとえば、実行時エラー '3707' です。  
  
-   負の値の 10 進数、完全なエラー番号を 10 進数に変換します。  
  
-   16 進数、完全なエラー番号の 16 進数表現です。 Windows 機能のコードは、4 番目の数字でです。 ADO エラー番号の機能のコードは*A*です。例: 0x800***A***0e7b がその例です。  
  
> [!NOTE]
>  OLE DB エラーは、ADO アプリケーションに渡すことができます。 通常、これらを特定するのには Windows 機能のコードの*4*です。 たとえば、0x800***4***です。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adErrBoundToCommand**|3707 -2146824581 0x800A0E7B|変更することはできません、 **ActiveConnection**のプロパティ、**レコード セット**を持つオブジェクト、**コマンド**オブジェクトのソースとして。|  
|**adErrCannotComplete**|3732 -2146824556 0x800A0E94|サーバーは、操作を完了できません。|  
|**adErrCantChangeConnection**|3748 -2146824540 0x800A0EA4|接続が拒否されました。 新しい接続を要求するには、既に使用されているものよりも異なる特性があります。|  
|**adErrCantChangeProvider**|3220 -2146825068 0X800A0C94|指定されたプロバイダーは、既に使用されているかによって異なります。|  
|**adErrCantConvertvalue**|3724 -2146824564 0x800A0E8C|符号の不一致またはデータ オーバーフロー以外の理由により、データ値を変換できません。 たとえば、変換がデータを切り詰めがあります。|  
|**adErrCantCreate**|3725 -2146824563 0x800A0E8D|データ値を設定またはフィールドのデータ型が不明か、プロバイダーには、操作を実行する十分なリソースが含まれているために取得できません。|  
|**adErrCatalogNotSet**|3747 -2146824541 0x800A0EA3|操作に必要ですが、有効な**ParentCatalog**です。|  
|**adErrColumnNotOnThisRow**|3726 -2146824562 0x800A0E8E|レコードでは、このフィールドは含まれません。|  
|**adErrDataConversion**|3421 -2146824867 0x800A0D5D|アプリケーションは、現在の操作で間違った型の値を使用します。|  
|**adErrDataOverflow**|3721 -2146824567 0x800A0E89|フィールドのデータ型で表されるデータ値が大きすぎます。|  
|**adErrDelResOutOfScope**|3738 -2146824550 0x800A0E9A|削除するオブジェクトの URL は、現在のレコードの範囲外です。|  
|**adErrDenyNotSupported**|3750 -2146824538 0x800A0EA6|プロバイダーは、共有の制限をサポートしていません。|  
|**adErrDenyTypeNotSupported**|3751 -2146824537 0x800A0EA7|プロバイダーは、要求された種類の制限を共有をサポートしていません。|  
|**adErrFeatureNotAvailable**|3251 -2146825037 0x800A0CB3|オブジェクトまたはプロバイダーでは、要求された操作を実行できません。|  
|**adErrFieldsUpdateFailed**|3749 -2146824539 0x800A0EA5|フィールドを更新できませんでした。 詳細については、確認、**ステータス**個々 のフィールド オブジェクトのプロパティです。|  
|**adErrIllegalOperation**|3219 -2146825069 0x800A0C93|操作は、このコンテキストでは許可されません。|  
|**adErrIntegrityViolation**|3719 -2146824569 0x800A0E87|データの値フィールドの整合性制約と競合しています。|  
|**adErrInTransaction**|3246 -2146825042 0x800A0CAE|**接続**トランザクションの実行中に、オブジェクトを明示的に閉じることができません。|  
|**adErrInvalidArgument**|3001 -2146825287 0x800A0BB9|個の引数は、正しくない型の許容範囲外または相互に競合がします。|  
|**adErrInvalidConnection**|3709 -2146824579 0x800A0E7D|接続を使用して、この操作を実行することはできません。 閉じているか、このコンテキストでは無効です。|  
|**adErrInvalidParamInfo**|3708 -2146824580 0x800A0E7C|**パラメーター**オブジェクトが正しく定義されていません。 一貫性のないまたは不完全な情報が提供されています。|  
|**adErrInvalidTransaction**|3714 -2146824574 0x800A0E82|トランザクションを調整するか、有効ではありませんが開始されていません。|  
|**adErrInvalidURL**|3729 -2146824559 0x800A0E91|URL には、無効な文字が含まれています。 URL が正しく入力されていることを確認してください。|  
|**adErrItemNotFound**|3265 -2146825023 0x800A0CC1|コレクション内の要求された名前または序数に対応する項目が見つかりません。|  
|**adErrNoCurrentRecord**|3021 -2146825267 0x800A0BCD|いずれか**BOF**または**EOF**が true の場合、または現在のレコードが削除されました。 要求された操作には、現在のレコードが必要です。|  
|**adErrNotExecuting**|3715 -2146824573 0x800A0E83|実行していないときに、操作を実行できません。|  
|**adErrNotReentrant**|3710 -2146824578 0x800A0E7E|イベント処理中に操作を実行することはできません。|  
|**adErrObjectClosed**|3704 -2146824584 0x800A0E78|オブジェクトが閉じられたときに、操作は許可されません。|  
|**adErrObjectInCollection**|3367 -2146824921 0x800A0D27|オブジェクトのコレクションは既にです。 追加できません。|  
|**adErrObjectNotSet**|3420 -2146824868 0x800A0D5C|オブジェクトが有効ではなくなりました。|  
|**adErrObjectOpen**|3705 -2146824583 0x800A0E79|オブジェクトが開いているときに、操作は許可されません。|  
|**adErrOpeningFile**|3002 -2146825286 0x800A0BBA|ファイルを開けませんでした。|  
|**adErrOperationCancelled**|3712 -2146824576 0x800A0E80|操作は、ユーザーによって取り消されました。|  
|**adErrOutOfSpace**|3734 -2146824554 0x800A0E96|操作を実行することはできません。 プロバイダーは、記憶域容量を取得できません。|  
|**adErrPermissionDenied**|3720 -2146824568 0x800A0E88|十分なアクセス許可には、フィールドへの書き込みができないようにします。|  
|**adErrProviderFailed**|3000 -2146825288 0x800A0BB8|プロバイダーは、要求された操作を実行できませんでした。|  
|**adErrProviderNotFound**|3706 -2146824582 0x800A0E7A|プロバイダーが見つかりません。 これがインストールされていない正常です。|  
|**adErrReadFile**|3003 -2146825285 0x800A0BBB|ファイルを読み取ることができませんでした。|  
|**adErrResourceExists**|3731 -2146824557 0x800A0E93|コピー操作を実行できません。 宛先の URL によって既にという名前のオブジェクトが存在します。 指定**adCopyOverwrite**オブジェクトを置換します。|  
|**adErrResourceLocked**|3730 -2146824558 0x800A0E92|指定された URL で表されるオブジェクトは、他の 1 つまたは複数のプロセスによってロックされています。 プロセスが終了するまで待機してから、操作を再試行してください。|  
|**adErrResourceOutOfScope**|3735 -2146824553 0x800A0E97|送信元または送信先の URL は、現在のレコードの範囲外です。|  
|**adErrSchemaViolation**|3722 -2146824566 0x800A0E8A|データ値は、データ型、またはフィールドの制約と競合しています。|  
|**adErrSignMismatch**|3723 -2146824565 0x800A0E8B|データ値は署名されましたが、プロバイダーによって使用されるフィールドのデータ型が署名されていなかったために、変換に失敗しました。|  
|**adErrStillConnecting**|3713 -2146824575 0x800A0E81|非同期の接続中には、操作を実行できません。|  
|**adErrStillExecuting**|3711 -2146824577 0x800A0E7F|非同期的に実行中には、操作を実行できません。|  
|**adErrTreePermissionDenied**|3728 -2146824560 0x800A0E90|権限はツリーまたはサブツリーにアクセスするのに十分ではありません。|  
|**adErrUnavailable**|3736 -2146824552 0x800A0E98|操作が完了しなかったし、状態を使用します。 フィールドを使用できないか、操作は試行されませんでした。|  
|**adErrUnsafeOperation**|3716 -2146824572 0x800A0E84|このコンピューターの安全性設定は、別のドメインのデータ ソースへのアクセスを防止します。|  
|**adErrURLDoesNotExist**|3727 -2146824561 0x800A0E8F|元の URL またはリンク先の URL の親のいずれかが存在しません。|  
|**adErrURLNamedRowDoesNotExist**|3737 -2146824551 0x800A0E99|この URL でという名前のレコードが存在しません。|  
|**adErrVolumeNotFound**|3733 -2146824555 0x800A0E95|プロバイダーは、URL で指定された記憶域デバイスを検索できません。 URL が正しく入力されていることを確認してください。|  
|**adErrWriteFile**|3004 -2146825284 0x800A0BBC|書き込みを file に失敗しました。|  
|**adWrnSecurityDialog**|3717 -2146824571 0x800A0E85|内部使用のみです。 使用しないでください。|  
|**adWrnSecurityDialogHeader**|3718 -2146824570 0x800A0E86|内部使用のみです。 使用しないでください。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
 ADO/WFC 同等の次のサブセットのみが定義されます。  
  
|定数|  
|--------------|  
|AdoEnums.ErrorValue.BOUNDTOCOMMAND|  
|AdoEnums.ErrorValue.DATACONVERSION|  
|AdoEnums.ErrorValue.FEATURENOTAVAILABLE|  
|AdoEnums.ErrorValue.ILLEGALOPERATION|  
|AdoEnums.ErrorValue.INTRANSACTION|  
|AdoEnums.ErrorValue.INVALIDARGUMENT|  
|AdoEnums.ErrorValue.INVALIDCONNECTION|  
|AdoEnums.ErrorValue.INVALIDPARAMINFO|  
|AdoEnums.ErrorValue.ITEMNOTFOUND|  
|AdoEnums.ErrorValue.NOCURRENTRECORD|  
|AdoEnums.ErrorValue.NOTEXECUTING|  
|AdoEnums.ErrorValue.NOTREENTRANT|  
|AdoEnums.ErrorValue.OBJECTCLOSED|  
|AdoEnums.ErrorValue.OBJECTINCOLLECTION|  
|AdoEnums.ErrorValue.OBJECTNOTSET|  
|AdoEnums.ErrorValue.OBJECTOPEN|  
|AdoEnums.ErrorValue.OPERATIONCANCELLED|  
|AdoEnums.ErrorValue.PROVIDERNOTFOUND|  
|AdoEnums.ErrorValue.STILLCONNECTING|  
|AdoEnums.ErrorValue.STILLEXECUTING|  
|AdoEnums.ErrorValue.UNSAFEOPERATION|  
  
## <a name="applies-to"></a>適用対象  
 [Number プロパティ (ADO)](../../../ado/reference/ado-api/number-property-ado.md)  
  
## <a name="see-also"></a>参照  
 [ADO エラー コード](../../../ado/guide/appendixes/ado-error-codes.md)
