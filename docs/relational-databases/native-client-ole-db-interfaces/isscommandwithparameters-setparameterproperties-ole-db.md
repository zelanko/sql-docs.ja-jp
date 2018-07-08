---
title: Isscommandwithparameters::setparameterproperties (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b4ccbc15cd4493f4d0d9654e9da130ac192f9f8c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416921"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a>ISSCommandWithParameters::SetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  序数順に各パラメーターのパラメーター プロパティを設定するか、SSPARAMPROPS 構造体の配列を指定して、一括でパラメーター プロパティを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT SetParameterProperties(  
      DB_UPARAMS cParams,   
      SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a>引数  
 *cParams*[in]  
 内の SSPARAMPROPS 数の構造体、 *rgParamProperties*配列。 この番号が 0 の場合**isscommandwithparameters::setparameterproperties**コマンドのパラメーターに指定されているすべてのプロパティが削除されます。  
  
 *rgParamProperties*[in]  
 設定する SSPARAMPROPS 構造体の配列。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **Isscommandwithparameters::setparameterproperties**メソッドは、主要な OLE DB と同じエラー コードを返します**icommandproperties::setproperties**メソッド。  
  
## <a name="remarks"></a>コメント  
 このメソッドを使用してパラメーターのプロパティを設定または許可されて各パラメーターの序数を 1 つの**isscommandwithparameters::setparameterproperties**プロパティ配列から SSPARAMPROPS が構築された 1 回呼び出します。  
  
 **SetParameterInfo**メソッドを呼び出す前に呼び出す必要があります、 **isscommandwithparameters::setparameterproperties**メソッド。 `SetParameterProperties(0, NULL)` を呼び出すと、指定したパラメーター プロパティがすべて消去されます。また、`SetParameterInfo(0,NULL,NULL)` を呼び出すと、パラメーターに関連付けられているすべてのプロパティを含めて、パラメーターに関するすべての情報が消去されます。  
  
 呼び出す**isscommandwithparameters::setparameterproperties**のない型のパラメーター プロパティを指定する dbtype_xml 型または DBTYPE_UDT 返します DB_E_ERRORSOCCURRED または DB_S_ERRORSOCCURRED とマーク、 *dwStatus* dbpropstatus_notset そのパラメーターの SSPARAMPROPS に含まれているすべてのときのフィールド。 DB_E_ERRORSOCCURRED または DB_S_ERRORSOCCURRED が指しているパラメーターを検出するには、SSPARAMPROPS に含まれている各 DBPROPSET の DBPROP 配列をすべて調べる必要があります。  
  
 場合**isscommandwithparameters::setparameterproperties**がパラメーター情報がまだ設定されていないパラメーターのプロパティを指定するために呼び出される**SetParameterInfo**プロバイダーは、e _ を返します。次のエラー メッセージで予期しない:  
  
 パラメーターを指定して SetParameterProperties メソッドを呼び出す場合は、最初に SetParameterInfo メソッドを呼び出す必要があります。 パラメーターのプロパティを設定する前に、パラメーター情報を設定する必要があります。  
  
 場合に呼び出し**isscommandwithparameters::setparameterproperties**パラメーター ヒントが設定されているいくつかのパラメーターといくつかのパラメーター、パラメーター ヒントが設定されていない、内の dwStatus プロパティが含まれています、SSPARAMPROPS プロパティ セットの DBPROPSET DBSTATUS_NOTSET が返されます。  
  
 SSPARAMPROPS 構造体は、次のように定義されています。  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 以降では、データベース エンジンの機能強化[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]isscommandwithparameters::setparameterproperties 期待どおりの結果のより正確な記述を取得できるようにします。 これらのより正確な結果の以前のバージョンの isscommandwithparameters::setparameterproperties によって返される値が異なる場合があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 詳細については、次を参照してください。[メタデータ検出](../../relational-databases/native-client/features/metadata-discovery.md)します。  
  
|Member|説明|  
|------------|-----------------|  
|*iOrdinal*|渡されるパラメーターの序数|  
|*cPropertySets*|DBPROPSET の数が含まれる構造*rgPropertySets*します。|  
|*rgPropertySets*|DBPROPSET 構造体の配列を返すメモリへのポインター|  
  
## <a name="see-also"></a>参照  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
