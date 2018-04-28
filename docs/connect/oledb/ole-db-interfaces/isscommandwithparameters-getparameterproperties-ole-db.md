---
title: Isscommandwithparameters::getparameterproperties (OLE DB) |Microsoft ドキュメント
description: ISSCommandWithParameters::GetParameterProperties (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- GetParameterProperties method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5c16b7902010a4030abc4166aab8ac9749e3cab5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

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
 SSPARAMPROPS 構造体の配列が返されるメモリへのポインター。 コンシューマーでこのメモリを解放する、プロバイダーを選択して、構造体のメモリを割り当てますこのメモリをアドレスを返します**imalloc::free**が不要になった必要がある場合、構造体。 呼び出しの前に**imalloc::free**の*prgParamProperties*、コンシューマーは、呼び出す必要がありますも**VariantClear**の*vValue*プロパティバリアントにはでの参照が含まれている場合に、メモリ リークを防ぐために各 DBPROP 構造体の BSTR などを入力します。 場合*pcParams*がゼロで出力または DB_E_ERRORSOCCURRED 以外のエラーが発生するプロバイダーは、メモリの割り当てはにより*prgParamProperties*出力に null ポインターです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **GetParameterProperties**メソッドは、主要な OLE DB と同じエラー コードを返します**icommandproperties::getproperties**その DB_S_ERRORSOCCURRED と db_e_errorsoccured は返す以外のメソッドにすることはできません発生します。  
  
## <a name="remarks"></a>解説  
 **Isscommandwithparameters::getparameterproperties**に関連するメソッドが、一貫した動作**GetParameterInfo**です。 場合[isscommandwithparameters::setparameterproperties](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)または**SetParameterInfo**呼び出されていないか、cParams に 0 を使用して呼び出されましたが**GetParameterInfo**パラメーター情報を派生し、それを取得します。 場合**isscommandwithparameters::setparameterproperties**または**SetParameterInfo**が少なくとも 1 つのパラメーター、呼び出された**isscommandwithparameters::getparameterproperties**メソッドでは、これらのパラメーターに対してのみプロパティを返しますを**isscommandwithparameters::setparameterproperties**が呼び出されています。 場合**isscommandwithparameters::setparameterproperties**後に呼び出されます**isscommandwithparameters::getparameterproperties**または**GetParameterInfo**、後続の呼び出し**isscommandwithparameters::getparameterproperties**をこれらのパラメーターの値が上書きを返す**isscommandwithparameters::setparameterproperties**メソッドが呼び出されました。  
  
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
 [ISSCommandWithParameters (&) #40";"OLE DB"&"#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
