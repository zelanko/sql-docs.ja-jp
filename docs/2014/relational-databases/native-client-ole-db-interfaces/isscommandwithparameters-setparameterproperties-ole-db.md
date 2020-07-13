---
title: ISSCommandWithParameters::SetParameterProperties (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
author: rothja
ms.author: jroth
ms.openlocfilehash: d141c1951066af14e25cb4dd36459f5e87051001
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85056077"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a>ISSCommandWithParameters::SetParameterProperties (OLE DB)
  序数順に各パラメーターのパラメーター プロパティを設定するか、SSPARAMPROPS 構造体の配列を指定して、一括でパラメーター プロパティを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT SetParameterProperties(  
DB_UPARAMS cParams,   
SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a>引数  
 *cParams*[in]  
 *rgParamProperties* 配列内の SSPARAMPROPS 構造体の数。 この数値が0の場合は、 `ISSCommandWithParameters::SetParameterProperties` コマンドのパラメーターに指定されている可能性のあるすべてのプロパティが削除されます。  
  
 *rgParamProperties*[in]  
 設定する SSPARAMPROPS 構造体の配列。  
  
## <a name="return-code-values"></a>リターン コードの値  
 この `ISSCommandWithParameters::SetParameterProperties` メソッドは、コア OLE DB **ICommandProperties:: SetProperties**メソッドと同じエラーコードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドを使用してパラメーターのプロパティを設定できるのは、序数によってパラメーターごとに指定するか、または `ISSCommandWithParameters::SetParameterProperties` SSPARC AMPROPS がプロパティ配列から構築された1回の呼び出しで許可されます。  
  
 メソッドを呼び出す前に**Setparameterinfo**メソッドを呼び出す必要があり `ISSCommandWithParameters::SetParameterProperties` ます。 `SetParameterProperties(0, NULL)` を呼び出すと、指定したパラメーター プロパティがすべて消去されます。また、`SetParameterInfo(0,NULL,NULL)` を呼び出すと、パラメーターに関連付けられているすべてのプロパティを含めて、パラメーターに関するすべての情報が消去されます。  
  
 `ISSCommandWithParameters::SetParameterProperties`を呼び出して、DBTYPE_XML 型または DBTYPE_UDT 型ではないパラメーターのプロパティを指定すると、DB_E_ERRORSOCCURRED または DB_S_ERRORSOCCURRED が返され、そのパラメーターの SSPARAMPROPS に含まれるすべての dbprops の*dwstatus*フィールドが DBPROPSTATUS_NOTSET でマークされます。 DB_E_ERRORSOCCURRED または DB_S_ERRORSOCCURRED が指しているパラメーターを検出するには、SSPARAMPROPS に含まれている各 DBPROPSET の DBPROP 配列をすべて調べる必要があります。  
  
 `ISSCommandWithParameters::SetParameterProperties`パラメーター情報が**setparameterinfo**でまだ設定されていないパラメーターのプロパティを指定するためにが呼び出された場合、プロバイダーは次のエラーメッセージと共に E_UNEXPECTED を返します。  
  
 パラメーターを指定して SetParameterProperties メソッドを呼び出す場合は、最初に SetParameterInfo メソッドを呼び出す必要があります。 パラメーターのプロパティを設定する前に、パラメーター情報を設定する必要があります。  
  
 パラメーターヒントが設定されているいくつかのパラメーターと、パラメーター情報が設定されていないパラメーターがの呼び出しに `ISSCommandWithParameters::SetParameterProperties` 含まれている場合、SDBPROPSET AMPROPS プロパティセットの dwStatus プロパティは DBSTATUS_NOTSET を返します。  
  
 SSPARAMPROPS 構造体は、次のように定義されています。  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降のデータベース エンジンの機能強化により、ISSCommandWithParameters::SetParameterProperties では、期待される結果のより正確な記述を取得できるようになりました。 結果がより正確になり、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で ISSCommandWithParameters::SetParameterProperties から返される値とは異なる可能性があります。 詳細については、「[メタデータの検出](../native-client/features/metadata-discovery.md)」を参照してください。  
  
|メンバー|説明|  
|------------|-----------------|  
|*iOrdinal*|渡されるパラメーターの序数|  
|*cPropertySets*|*rgPropertySets* 内の DBPROPSET 構造体の数|  
|*rgPropertySets*|DBPROPSET 構造体の配列を返すメモリへのポインター|  
  
## <a name="see-also"></a>参照  
 [ISSCommandWithParameters &#40;OLE DB&#41;](isscommandwithparameters-ole-db.md)  
  
  
