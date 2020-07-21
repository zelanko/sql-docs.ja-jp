---
title: '&lt;xsd:redefine&gt; 要素 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xsd:redefine element
ms.assetid: 5f3e9b65-f10e-4db2-a62c-b270ac11d04e
author: rothja
ms.author: jroth
ms.openlocfilehash: ce439e81cf87e97b4afe6e25a201e1ab0cb2a458
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059473"
---
# <a name="the-ltxsdredefinegt-element"></a>&lt;xsd:redefine&gt; 要素
  W3C XSD の **redefine** 要素は、スキーマ コンポーネントの再定義をサポートします。 ただし、このディレクティブのサポートはパフォーマンスが低下する可能性があり、再定義された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `xml` スキーマに関連付けられているデータ型のすべてのインスタンスを再検証する必要もあります。 このため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではこれらの要素をサポートしません。 要素を含む XML スキーマ **\<xsd:redefine>** はサーバーによって拒否されます。  
  
 スキーマまたはスキーマ コンポーネントを更新するには、代わりに次の方法を使用できます。  
  
1.  変更されたスキーマ コンポーネントを使用して新しい XML スキーマ コレクションを作成します。  
  
2.  `xml`新しい Xml スキーマコレクションを使用するように、再定義する Xml スキーマコレクションを使用するすべてのデータ型 (XML DT) を再入力します。 そのためには、ALTER TABLE コマンドの ALTER COLUMN オプションを使用して列の型を再指定するか、変数やパラメーターの XML スキーマ コレクション制約を変更します。  
  
3.  古いバージョンの XML スキーマ コレクションを削除します。  
  
## <a name="see-also"></a>参照  
 [サーバー上の XML スキーマ コレクションの要件と制限](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
