---
title: "コレクション (Visual C++ 構文のインデックス #import) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
dev_langs: C++
helpviewer_keywords:
- 'syntax indexes [ADO], ADO for Visual C++ syntax with #import'
- 'collections [ADO], ADO for Visual C++ syntax with #import'
- 'ADO for Visual C++ syntax with #import [ADO]'
- '#import [ADO]'
ms.assetid: 36fbca8e-1884-44b5-806b-d15e30f42fe6
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d4f4f89342ddf85459779c77ecc11f7059734aa7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="collections-visual-c-syntax-index-with-import"></a>コレクション (Visual C++ 構文のインデックス #import)
コレクションが、一般的なメソッドとプロパティを継承ことを確認すると便利です。  
  
 すべてのコレクションの継承、**カウント**プロパティおよび**更新**メソッド、およびすべてのコレクションを追加、**項目**プロパティです。 **エラー**コレクションを追加、**クリア**メソッドです。 **パラメーター**コレクションの継承、 **Append**と**削除**メソッド、中に、**フィールド**コレクションに追加、 **Append**、**削除**、および**更新**メソッドです。  
  
## <a name="properties-collection"></a>プロパティのコレクション  
  
### <a name="methods"></a>メソッド  
  
```  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>[プロパティ]  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="errors-collection"></a>Errors コレクション  
  
### <a name="methods"></a>メソッド  
  
```  
HRESULT Clear( );  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>[プロパティ]  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="parameters-collection"></a>Parameters コレクション  
  
### <a name="methods"></a>メソッド  
  
```  
HRESULT Append( IDispatch * Object );  
HRESULT Delete( const _variant_t & Index );  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>[プロパティ]  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="fields-collection"></a>Fields コレクション  
  
### <a name="methods"></a>メソッド  
  
```  
HRESULT Append( _bstr_t Name, enum DataTypeEnum Type, long DefinedSize, enum FieldAttributeEnum Attrib, const _variant_t & FieldValue = vtMissing );  
HRESULT Delete( const _variant_t & Index );  
HRESULT Refresh( );  
HRESULT Update( );  
```  
  
### <a name="properties"></a>[プロパティ]  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="see-also"></a>参照  
 [Errors コレクション (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
