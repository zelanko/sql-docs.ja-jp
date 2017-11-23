---
title: "つまりメソッド (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Record::raw_CopyRecord
- _Record::CopyRecord
helpviewer_keywords: CopyRecord method [ADO]
ms.assetid: b9bcf272-3c74-479f-95dd-0229a32e98fc
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9459d144016deaaec593a8edd92bf5b518a8962b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="copyrecord-method-ado"></a>つまりメソッド (ADO)
によって表されるエンティティのコピー、[レコード](../../../ado/reference/ado-api/record-object-ado.md)別の場所にします。  
  
## <a name="syntax"></a>構文  
  
```  
  
Record.CopyRecord (Source, Destination, UserName, Password, Options, Async)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ソース*  
 省略可。 A**文字列**URL を含むエンティティを指定することをコピーする (たとえば、ファイルまたはディレクトリ) の値。 場合*ソース*を省略するか、空の文字列、ファイルまたはディレクトリが現在によって表される指定[レコード](../../../ado/reference/ado-api/record-object-ado.md)コピーされます。  
  
 *変換先*  
 省略可。 A**文字列**場所を指定する URL を含む値で*ソース*コピーされます。  
  
 *UserName*  
 省略可。 A**文字列**が必要な場合へのアクセスを許可するユーザー ID を表す値*先*です。  
  
 *Password*  
 省略可。 A**文字列**必要な場合は、以下のことを確認するためのパスワードを表す値*UserName*です。  
  
 *および*  
 省略可。 A [CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md)の既定値を持つ値**adCopyUnspecified**です。 このメソッドの動作を指定します。  
  
 *非同期*  
 省略可。 A**ブール**値と**True**、この操作を非同期にすることを指定します。  
  
## <a name="return-value"></a>戻り値  
 A**文字列**値を通常の値を返します*先*です。 ただし、返される正確な値は、プロバイダーによって異なります。  
  
## <a name="remarks"></a>解説  
 値*ソース*と*先*することはできませんと同じです。 それ以外の場合、実行時エラーが発生します。 少なくとも 1 つのサーバー、パス、またはリソースの名前が異なる必要があります。  
  
 すべての子 (たとえば、サブディレクトリ)*ソース*しない限り、コピーされた再帰的には、 **adCopyNonRecursive**を指定します。 操作では再帰的な*先*のサブディレクトリではない必要があります*ソース*です。 それ以外の場合、操作を完了できません。  
  
 このメソッドは失敗*先*しない限り (たとえば、ファイルまたはディレクトリ)、既存のエンティティを識別**adCopyOverWrite**が指定されています。  
  
> [!IMPORTANT]
>  使用して、 **adCopyOverWrite**慎重に行うオプションします。 ディレクトリにファイルをコピーするときに、このオプションを指定するたとえば、*削除*ディレクトリ ファイルに置き換えます。  
  
> [!NOTE]
>  Http スキームを使用する Url が自動的に起動、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 詳細については、次を参照してください。[絶対と相対 Url](../../../ado/guide/data/absolute-and-relative-urls.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
