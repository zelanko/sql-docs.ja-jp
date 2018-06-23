---
title: Isscommandwithparameters::setparameterproperties (OLE DB) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.openlocfilehash: 10b24720130c720a3b53fb879068a37abf2570f6
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35699563"
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
 数、SSPARAMPROPS 構造体に、 *rgParamProperties*配列。 この数が 0 の場合**isscommandwithparameters::setparameterproperties**コマンドのパラメーターの指定されたすべてのプロパティが削除されます。  
  
 *rgParamProperties*[in]  
 設定する SSPARAMPROPS 構造体の配列。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **Isscommandwithparameters::setparameterproperties**メソッドは、主要な OLE DB と同じエラー コードを返します**icommandproperties::setproperties**メソッドです。  
  
## <a name="remarks"></a>コメント  
 このメソッドを使用してパラメーター プロパティを設定または許可されて、各パラメーターごとに、序数を 1 つの**isscommandwithparameters::setparameterproperties**プロパティ配列から SSPARAMPROPS が構築された 1 回呼び出します。  
  
 **SetParameterInfo**メソッドを呼び出す前に呼び出す必要があります、 **isscommandwithparameters::setparameterproperties**メソッドです。 `SetParameterProperties(0, NULL)` を呼び出すと、指定したパラメーター プロパティがすべて消去されます。また、`SetParameterInfo(0,NULL,NULL)` を呼び出すと、パラメーターに関連付けられているすべてのプロパティを含めて、パラメーターに関するすべての情報が消去されます。  
  
 呼び出す**isscommandwithparameters::setparameterproperties**はない型のパラメーターのプロパティを指定する dbtype_xml 型または dbtype_udt 型を返します DB_E_ERRORSOCCURRED または DB_S_ERRORSOCCURRED とマーク、 *dwStatus* dbpropstatus_notset そのパラメーターの SSPARAMPROPS に含まれているすべての Dbprop のフィールドです。 DB_E_ERRORSOCCURRED または DB_S_ERRORSOCCURRED が指しているパラメーターを検出するには、SSPARAMPROPS に含まれている各 DBPROPSET の DBPROP 配列をすべて調べる必要があります。  
  
 場合**isscommandwithparameters::setparameterproperties**がパラメーター ヒントがまだ設定されていないパラメーターのプロパティを指定するために呼び出される**SetParameterInfo**プロバイダーは、e _ を返します。次のエラー メッセージで予期しない:  
  
 パラメーターを指定して SetParameterProperties メソッドを呼び出す場合は、最初に SetParameterInfo メソッドを呼び出す必要があります。 パラメーターのプロパティを設定する前に、パラメーター情報を設定する必要があります。  
  
 場合に呼び出し**isscommandwithparameters::setparameterproperties**パラメーター情報が、セットされているが、一部のパラメーターといくつかのパラメーター、パラメーター情報が設定されていない、内の dwStatus プロパティが含まれています、SSPARAMPROPS プロパティ セットの DBPROPSET DBSTATUS_NOTSET が返されます。  
  
 SSPARAMPROPS 構造体は、次のように定義されています。  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 以降で、データベース エンジンの機能強化[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]isscommandwithparameters::setparameterproperties を期待する結果のより正確な記述を取得できるようにします。 以前のバージョンの isscommandwithparameters::setparameterproperties によって返される値からこれらのより正確な結果が異なる場合があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 詳細については、次を参照してください。[メタデータ検出](../../relational-databases/native-client/features/metadata-discovery.md)です。  
  
|Member|説明|  
|------------|-----------------|  
|*iOrdinal*|渡されるパラメーターの序数|  
|*cPropertySets*|DBPROPSET の数が構造体に*rgPropertySets*です。|  
|*rgPropertySets*|DBPROPSET 構造体の配列を返すメモリへのポインター|  
  
## <a name="see-also"></a>参照  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
