---
title: sql:identity 注釈と sql:guid 注釈の使用
description: XSD スキーマで sql:identity および sql:guid 注釈を使用して XML 更新グラムの動作を定義する方法について説明します。
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:guid
- annotated XSD schemas, IDENTITY-type columns
- annotated XSD schemas, GUID values
- DiffGrams [SQLXML], annotations
- identity annotation
- XSD schemas [SQLXML], GUID values
- GUIDs [SQLXML]
- guid annotation
- sql:identity
- IDENTITY-type column
- XSD schemas [SQLXML], IDENTITY-type columns
- updategrams [SQLXML], GUID values
ms.assetid: 7661dfd0-6573-4692-a8f1-3597adcd33c4
author: MightyPen
ms.author: genemi
ms.reviewer: ''
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f581c1a5c0d925d48df5a16d95cdb141e2d48f83
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388103"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a>sql:identity 注釈と sql:guid 注釈の使用
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  の[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース列にマップする任意のノードの XSD スキーマで **、sql:identity**および**sql:guid**アノテーションを指定できます。 アップデートグラム形式は**updg:at-identity**属性と**updg:guid**属性をサポートしていますが、DiffGram 形式はサポートしていません。 **updg:at-identity**属性は、IDENTITY タイプの列を更新する際の動作を定義します。 **updg:guid**属性を使用すると、GUID 値を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]取得し、アップデートグラムで使用できます。 詳細および動作するサンプルについては、「 [SQLXML 4.0&#41;&#40;XML 更新グラムを使用したデータの挿入](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)」を参照してください。  
  
 **sql:ID**および**sql:guid**アノテーションは、この機能を DiffGrams に拡張します。  
  
 DiffGram を実行すると、DiffGram がアップデートグラムに変換された後、アップデートグラムが実行されます。 XSD スキーマで**sql:identity**および**sql:guid**アノテーションを指定することにより、実際にはアップデートグラムの動作を定義します。 したがって、すべての注釈はアップデートグラムのコンテキストで記述します。 これらの注釈は DiffGram とアップデートグラムの両方で使用できますが、アップデートグラムには ID 値と GUID 値をより効率的に処理する機能が既に用意されています。  
  
 **sql:id**および**sql:guid**注釈は、複合コンテンツ要素で定義できます。  
  
## <a name="sqlidentity-annotation"></a>sql:identity 注釈  
 IDENTITY タイプのデータベース列にマップする任意のノードの XSD スキーマで**sql:IDENTITY**アノテーションを指定できます。 このアノテーションに指定された値は、IDENTITY タイプの列の更新方法を定義します (更新グラムで指定された値を使用して列を変更するか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]値を無視します)。  
  
 **sql:ID**アノテーションには、次の 2 つの値を割り当てることができます。  
  
 ignore  
 アップデートグラムで列に提供される値を無視し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で生成される ID 値を使用します。  
  
 useValue  
 アップデートグラムで提供される値を使用して、IDENTITY 型列を更新します。 アップデートグラムでは、列が ID 値かどうかは確認されません。  
  
 アップデートグラムで IDENTITY 型列の値を指定する場合は、スキーマで**sql:identity="useValue" を**指定する必要があります。  
  
## <a name="sqlguid-annotation"></a>sql:guid 注釈  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で GUID 値を生成し、その値をアップデートグラムで使用できます。 DiffGrams のコンテキストでは **、sql:guid**注釈を使用して、SQL Server によって生成される GUID 値を使用するか、その列の更新グラムで指定されている値を使用するかを指定できます。  
  
 **sql:guid**アノテーションには、次の 2 つの値を割り当てることができます。  
  
 generate  
 更新操作で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で生成される GUID を列に使用することを指定します。  
  
 useValue  
 アップデートグラムで提供される値を列に使用することを指定します。 これが既定値です。  
  
  
