---
title: Isscommandwithparameters::getparameterproperties (OLE DB) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f06c97d1f6d1e477700117c3038d0186db085fd1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075714"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
  SSPARAMPROPS プロパティ セット構造体の配列を返します。各 UDT または XML パラメーターごとに 1 つの SSPARAMPROPS プロパティ セットが返されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT GetParameterProperties(  
DB_UPARAMS *pcParams,  
SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a>引数  
 *pcParams*[in] には、[出力].  
 返された SSPARAMPROPS 構造体の番号が含まれるメモリへのポインター *prgParamProperties*です。  
  
 *prgParamProperties*[out]  
 SSPARAMPROPS 構造体の配列が返されるメモリへのポインター。 プロバイダーを選択して、構造体のメモリを割り当てますアドレスです。 このメモリを返しますコンシューマーでこのメモリを解放する**imalloc::free**が不要になった必要がある場合、構造体。 呼び出しの前に**imalloc::free**の*prgParamProperties*、コンシューマーは、呼び出す必要がありますも**VariantClear**の*vValue*プロパティバリアントにはでの参照が含まれている場合に、メモリ リークを防ぐために各 DBPROP 構造体の型 (BSTR です。)場合*pcParams*ゼロに出力されるか DB_E_ERRORSOCCURRED 以外のエラーが発生する、プロバイダーのメモリを割り当てられません、確実に*prgParamProperties*出力に null ポインターです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **GetParameterProperties**メソッドは、主要な OLE DB と同じエラー コードを返します**icommandproperties::getproperties**その DB_S_ERRORSOCCURRED と db_e_errorsoccured は返す以外のメソッドにすることはできません発生します。  
  
## <a name="remarks"></a>コメント  
 **Isscommandwithparameters::getparameterproperties**に関して、一貫した動作**GetParameterInfo**です。 場合[isscommandwithparameters::setparameterproperties](isscommandwithparameters-setparameterproperties-ole-db.md)または**SetParameterInfo**呼び出されていないか、cParams に 0 を使用して呼び出されましたが**GetParameterInfo**パラメーター情報を派生し、これを返します。 場合**isscommandwithparameters::setparameterproperties**または**SetParameterInfo**が少なくとも 1 つのパラメーター、呼び出された**isscommandwithparameters::getparameterproperties**をこれらのパラメーターに対してのみプロパティを返します**isscommandwithparameters::setparameterproperties**が呼び出されています。 場合**isscommandwithparameters::setparameterproperties**後に呼び出されます**isscommandwithparameters::getparameterproperties**または**GetParameterInfo**、後続の呼び出し**isscommandwithparameters::getparameterproperties**をこれらのパラメーターの値が上書きを返す**isscommandwithparameters::setparameterproperties**が呼び出されています。  
  
 SSPARAMPROPS 構造体は、次のように定義されています。  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|Member|説明|  
|------------|-----------------|  
|*iOrdinal*|渡されるパラメーターの序数|  
|*cPropertySets*|DBPROPSET の数が構造体に*rgPropertySets*です。|  
|*rgPropertySets*|DBPROPSET 構造体の配列を返すメモリへのポインター|  
  
## <a name="see-also"></a>参照  
 [ISSCommandWithParameters &#40;OLE DB&#41;](isscommandwithparameters-ole-db.md)  
  
  