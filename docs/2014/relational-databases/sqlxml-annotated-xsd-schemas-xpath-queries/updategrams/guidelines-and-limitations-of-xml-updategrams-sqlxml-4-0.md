---
title: XML アップデートグラムのガイドラインと制限事項 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 953fc5b7c203faa8fa6a9820993a3d0fd7a7de40
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66014828"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a>XML アップデートグラムのガイドラインと制限 (SQLXML 4.0)
  XML アップデートグラムを使用する場合は、次の点に注意してください。  
  
-   1組だけを持つ挿入操作のためのアップデートグラムを使用している場合は、>と** \<>** ブロックの後** \<に**、 ** \<>前**のブロックを省略できます。 逆に、削除操作の場合は、 ** \<after>** ブロックを省略できます。  
  
-   ** \<以前**に複数のアップデートグラムを使用していて、 ** \<同期>** タグで** \<>** ブロックを>している場合は、 ** \<>** ブロックの**前と\<>** のブロックの後の両方で、>と** \<>のペアの** ** \<前に**形成するように指定する必要があります。  
  
-   アップデートグラムの更新は、XML スキーマで提供される XML ビューに適用されます。 したがって、既定のマッピングが正しく行われるようにするには、アップデートグラムでスキーマ ファイル名を指定するか、ファイル名を指定しない場合は、要素名と属性名がデータベースのテーブル名と列名に一致している必要があります。  
  
-   SQLXML 4.0 を使用する場合、アップデートグラムのすべての列値は、子要素の XML ビューを構成するために提供される XDR スキーマまたは XSD スキーマで明示的にマップする必要があります。 この動作は以前のバージョンの SQLXML とは異なります。以前のバージョンでは、`sql:relationship` 注釈で列の値が外部キーの一部として暗黙的に指定されていれば、スキーマでマップされない列値も許可されていました。 この変更は、子要素への主キー値の割り当てには影響しません。SQLXML 4.0 では、子要素に対して明示的に値が指定されていない場合でも、値が割り当てられます。  
  
-   アップデートグラムを使用してバイナリ列 ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `image`データ型など) のデータを変更する場合は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型 (など`sql:datatype="image"`) と XML データ型 (たとえば、 `dt:type="binhex"`や`dt:type="binbase64`) を指定するマッピングスキーマを指定する必要があります。 バイナリ列のデータは、アップデートグラム内に指定する必要があります。マッピング スキーマで指定される `sql:url-encode` 注釈は、アップデートグラムでは無視されます。  
  
-   XSD スキーマを記述するときに、`sql:relation` 注釈または `sql:field` 注釈に指定する値に特殊文字が含まれる場合、たとえば、スペースを含むテーブル名 "Order Details" を指定する場合などは、値を "[Order Details]" のように角かっこで囲む必要があります。  
  
-   アップデートグラムの使用で、チェーン リレーションシップはサポートされません。 たとえば、テーブル A とテーブル C が、テーブル B を使用するチェーン リレーションシップで関連付けられている場合は、アップデートグラムの実行時に次のエラーが発生します。  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     スキーマとアップデートグラムの両方が正しく、有効な形式であっても、チェーン リレーションシップが存在すると、このエラーが発生します。  
  
-   アップデートグラムでは、更新中に `image` 型データをパラメーターとして引き渡すことはできません。  
  
-   やイメージのような`text/ntext`バイナリラージオブジェクト (BLOB) 型は、updategrams を使用する場合に、 ** \<の前の>** ブロックでは使用しないでください。これには、同時実行制御に使用するものが含まれます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で、BLOB 型の比較の制限によって問題が発生する可能性があります。 たとえば、`text` データ型の列を比較するには WHERE 句で LIKE キーワードを使用しますが、データ サイズが 8 KB を超える BLOB 型の場合、この比較は失敗します。  
  
-   `ntext` データで特殊文字を使用すると、BLOB 型の比較の制限によって、SQLXML 4.0 で問題が発生する可能性があります。 たとえば、アップデートグラムの** \<before>** ブロックで "[Serializable]" を使用した場合、型の`ntext`列の同時実行制御チェックでは、次の SQLOLEDB エラーの説明で失敗します。  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a>参照  
 [SQLXML 4.0&#41;&#40;アップデートグラムのセキュリティに関する考慮事項](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
