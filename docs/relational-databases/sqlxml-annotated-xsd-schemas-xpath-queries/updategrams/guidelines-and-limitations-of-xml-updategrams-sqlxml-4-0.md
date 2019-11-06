---
title: XML アップデート グラム (SQLXML 4.0) のガイドラインと制限 |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: eb8a2a978e70b5148b78f394cf0d8413d5769c64
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086848"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a>XML アップデートグラムのガイドラインと制限 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  XML アップデートグラムを使用する場合は、次の点に注意してください。  
  
-   1 つのペアのみを使用して、挿入操作のアップデート グラムを使用している場合 **\<する前に >** と **\<後 >** 、ブロック、 **\<する前に>** ブロックを省略できます。 逆に、削除操作が発生した場合、 **\<後 >** ブロックを省略できます。  
  
-   複数のアップデート グラムを使用している場合 **\<する前に >** と **\<後 >** 内のブロック、 **\<同期 >** 両方のタグ **\<する前に >** ブロックと **\<後 >** フォームにブロックを指定する必要があります **\<する前に >** と **\<後 >** ペア。  
  
-   アップデートグラムの更新は、XML スキーマで提供される XML ビューに適用されます。 したがって、既定のマッピングが正しく行われるようにするには、アップデートグラムでスキーマ ファイル名を指定するか、ファイル名を指定しない場合は、要素名と属性名がデータベースのテーブル名と列名に一致している必要があります。  
  
-   SQLXML 4.0 を使用する場合、アップデートグラムのすべての列値は、子要素の XML ビューを構成するために提供される XDR スキーマまたは XSD スキーマで明示的にマップする必要があります。 この動作は以前のバージョンの SQLXML の外部キーの一部としては、暗黙的であった場合、スキーマにマップされていない列の値が許可されているが、 **sql:relationship**注釈。 この変更は、子要素への主キー値の割り当てには影響しません。SQLXML 4.0 では、子要素に対して明示的に値が指定されていない場合でも、値が割り当てられます。  
  
-   バイナリ列のデータを変更するアップデート グラムを使用している場合 (など、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **イメージ**データ型)、マッピング スキーマで指定する必要があります、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型 (たとえば、 **sql:datatype =「イメージ」** ) と、XML データ型 (たとえば、 **dt:type ="binhex"** または**dt:type ="binbase64**) 指定する必要があります。 は、アップデート グラムには、バイナリ列のデータを指定する必要があります**sql:url-エンコード**アップデート グラムでマッピング スキーマで指定されている注釈は無視されます。  
  
-   値を指定する場合、XSD スキーマを記述するとき、 **sql:relation**または**sql:field**注釈には、(たとえば、"Order Details"にある空白文字などの特殊文字が含まれています。テーブル名の場合)、この値は (たとえば、"[Order Details]") の角かっこで囲む必要があります。  
  
-   アップデートグラムの使用で、チェーン リレーションシップはサポートされません。 たとえば、テーブル A とテーブル C が、テーブル B を使用するチェーン リレーションシップで関連付けられている場合は、アップデートグラムの実行時に次のエラーが発生します。  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     スキーマとアップデートグラムの両方が正しく、有効な形式であっても、チェーン リレーションシップが存在すると、このエラーが発生します。  
  
-   アップデート グラムに渡すことが許可されていない**イメージ**の更新中にパラメーターとしてデータを入力します。  
  
-   バイナリ ラージ オブジェクト (BLOB) のような種類**text、ntext**でイメージを使用する必要があります、 **\<する前に >** で使用するために含まれてはこのため、アップデート グラムを使用する場合ブロック同時実行制御。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で、BLOB 型の比較の制限によって問題が発生する可能性があります。 列の比較するには、WHERE 句で LIKE キーワードが使用されるなど、**テキスト**データを入力します。 ただし、比較は失敗、データのサイズが 8 K を超える BLOB 型の場合。  
  
-   特殊文字**ntext**データ BLOB 型の比較の制限により SQLXML 4.0 で問題が発生することができます。 "[Serializable]"の使用など、 **\<する前に >** 同時実行制御の列のチェックで使用する場合は、アップデート グラムのブロック**ntext**型は、次の SQLOLEDB で失敗エラーの説明:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a>関連項目  
 [アップデート グラムのセキュリティに関する考慮事項&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
