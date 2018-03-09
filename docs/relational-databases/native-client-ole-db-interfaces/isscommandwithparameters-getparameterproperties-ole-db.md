---
title: "Isscommandwithparameters::getparameterproperties (OLE DB) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5a157de9b398914ce7dd9648cfd5612ffbf48a6a
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

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
 SSPARAMPROPS 構造体の配列が返されるメモリへのポインター。 プロバイダーを選択して、構造体のメモリを割り当てますアドレスです。 このメモリを返しますコンシューマーでこのメモリを解放する**imalloc::free**が不要になった必要がある場合、構造体。 呼び出しの前に**imalloc::free**の*prgParamProperties*、コンシューマーは、呼び出す必要がありますも**VariantClear**の*vValue*バリアントにはで、参照型 (BSTR です) などが含まれている場合に、メモリ リークを防ぐために各 DBPROP 構造体のプロパティ。場合*pcParams*ゼロに出力されるか DB_E_ERRORSOCCURRED 以外のエラーが発生する、プロバイダーのメモリを割り当てられません、確実に*prgParamProperties*出力に null ポインターです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **GetParameterProperties**メソッドは、主要な OLE DB と同じエラー コードを返します**icommandproperties::getproperties**その DB_S_ERRORSOCCURRED と db_e_errorsoccured は返す以外のメソッドを発生させることはできません。  
  
## <a name="remarks"></a>解説  
 **Isscommandwithparameters::getparameterproperties**に関して、一貫した動作**GetParameterInfo**です。 場合[isscommandwithparameters::setparameterproperties](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)または**SetParameterInfo**呼び出されていないか、cParams に 0 を使用して呼び出されましたが**GetParameterInfo**パラメーター情報を派生し、これを返します。 場合**isscommandwithparameters::setparameterproperties**または**SetParameterInfo**が少なくとも 1 つのパラメーター、呼び出された**isscommandwithparameters::getparameterproperties**をこれらのパラメーターに対してのみプロパティを返します**isscommandwithparameters::setparameterproperties**呼び出されました。 場合**isscommandwithparameters::setparameterproperties**後に呼び出されます**isscommandwithparameters::getparameterproperties**または**GetParameterInfo**後続の呼び出しを**isscommandwithparameters::getparameterproperties**をこれらのパラメーターの値が上書きを返す**isscommandwithparameters::setparameterproperties**が呼び出されました。  
  
 SSPARAMPROPS 構造体は、次のように定義されています。  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|メンバー|Description|  
|------------|-----------------|  
|*iOrdinal*|渡されるパラメーターの序数|  
|*cPropertySets*|DBPROPSET の数が構造体に*rgPropertySets*です。|  
|*rgPropertySets*|DBPROPSET 構造体の配列を返すメモリへのポインター|  
  
## <a name="see-also"></a>参照  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
