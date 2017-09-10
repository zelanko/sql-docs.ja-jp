---
title: "ALTER ASSEMBLY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_ASSEMBLY_TSQL
- ALTER ASSEMBLY
dev_langs:
- TSQL
helpviewer_keywords:
- assemblies [CLR integration], modifying
- refreshing assemblies
- assemblies [CLR integration], versioning
- assemblies [CLR integration], adding files
- modifying assemblies
- adding files
- ALTER ASSEMBLY statement
ms.assetid: 87bca678-4e79-40e1-bb8b-bd5ed8f34853
caps.latest.revision: 76
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4b69c3ea4cc94c6b0b318cc13453d9d04b57df0b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-assembly-transact-sql"></a>ALTER ASSEMBLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  変更することにより、アセンブリを変更、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]カタログ アセンブリのプロパティです。 ALTER ASSEMBLY がの最新のコピーを更新、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]実装を保持し、追加または関連付けられているファイルを削除するモジュールです。 アセンブリを使用して作成される[CREATE ASSEMBLY](../../t-sql/statements/create-assembly-transact-sql.md)です。  

>  [!WARNING]
>  CLR では、セキュリティ境界としてサポートされなくなった、.NET Framework のコード アクセス セキュリティ (CAS) が使用されます。 `PERMISSION_SET = SAFE` で作成された CLR アセンブリが、外部のシステム リソースにアクセスし、非管理対象コードを呼び出し、sysadmin 特権を取得できる場合があります。 [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] 以降、CLR アセンブリのセキュリティを強化するために `clr strict security` という `sp_configure` オプションが導入されました。 `clr strict security` は既定で有効になり、`SAFE` および `EXTERNAL_ACCESS` アセンブリを `UNSAFE` とマークされている場合と同様に扱います。 `clr strict security` オプションは、旧バージョンとの互換性のために無効にできますが、これは推奨されません。 Microsoft では、master データベースで `UNSAFE ASSEMBLY` アクセス許可が付与されている対応するログインを含む証明書または非対称キーで、すべてのアセンブリに署名することをお勧めします。 詳しくは、「[CLR の厳密なセキュリティ](../../database-engine/configure-windows/clr-strict-security.md)」をご覧ください。  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ALTER ASSEMBLY assembly_name  
    [ FROM <client_assembly_specifier> | <assembly_bits> ]  
    [ WITH <assembly_option> [ ,...n ] ]  
    [ DROP FILE { file_name [ ,...n ] | ALL } ]  
    [ ADD FILE FROM   
    {   
        client_file_specifier [ AS file_name ]   
      | file_bits AS file_name   
    } [,...n ]   
    ] [ ; ]  
<client_assembly_specifier> :: =  
    '\\computer_name\share-name\[path\]manifest_file_name'  
  | '[local_path\]manifest_file_name'  
  
<assembly_bits> :: =  
    { varbinary_literal | varbinary_expression }  
  
<assembly_option> :: =  
    PERMISSION_SET = { SAFE | EXTERNAL_ACCESS | UNSAFE }   
  | VISIBILITY = { ON | OFF }  
  | UNCHECKED DATA  
  
```  
  
## <a name="arguments"></a>引数  
 *アセンブリ名*  
 変更するアセンブリの名前を指定します。 *アセンブリ名*データベースに既に存在する必要があります。  
  
 \<Client_assembly_specifier > |\<assembly_bits >  
 最新のコピーにアセンブリを更新、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]実装を保持するモジュールです。 このオプションを使用できるのは、指定したアセンブリに関連付けられているファイルが存在しない場合だけです。  
  
 \<client_assembly_specifier > ネットワークまたは更新するアセンブリが配置されているローカルの場所を指定します。 ネットワーク上の場所を指定する場合は、コンピューター名、共有名、および共有内のパスを指定します *manifest_file_name*アセンブリのマニフェストを含むファイルの名前を指定します。  
  
 \<assembly_bits > はアセンブリのバイナリ値。  
  
 更新も必要な依存アセンブリに対して、個別の ALTER ASSEMBLY ステートメントを実行する必要があります。  
  
 PERMISSION_SET = { SAFE | EXTERNAL_ACCESS | UNSAFE }   
>  [!IMPORTANT]  
>  `PERMISSION_SET`オプションの影響を受けました、`clr strict security`オプション、opening 警告で説明します。 ときに`clr strict security`が有効になっている、すべてのアセンブリとして扱われます`UNSAFE`です。  
 アセンブリの [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] コード アクセス権セットのプロパティを指定します。 このプロパティの詳細については、次を参照してください。 [CREATE ASSEMBLY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-assembly-transact-sql.md).  
  
> [!NOTE]  
>  EXTERNAL_ACCESS および UNSAFE オプションは、包含データベースでは使用できません。  
  
 VISIBILITY = { ON | OFF }   
 アセンブリに対する共通言語ランタイム (CLR) 関数、ストアド プロシージャ、トリガー、ユーザー定義型、およびユーザー定義集計関数の作成時に、そのアセンブリが表示されるかどうかを指定します。 OFF に設定した場合、アセンブリは、他のアセンブリによってのみ呼び出されます。 アセンブリに対して既に作成された CLR データベース オブジェクトが存在する場合、そのアセンブリの表示は変更できません。 によって参照されるアセンブリ*assembly_name*既定で非表示としてアップロードされます。  
  
 UNCHECKED DATA   
 既定では、個々のテーブル行の一貫性を検証する必要がある場合、ALTER ASSEMBLY は失敗します。 このオプションを指定すると、DBCC CHECKTABLE によって、この検証を延期することができます。 これを指定した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、データベースのテーブルに次のデータが含まれていても、ALTER ASSEMBLY ステートメントが実行されます。  
  
-   保存される計算列を直接または間接的にを通じて、アセンブリ内のメソッドを参照する[!INCLUDE[tsql](../../includes/tsql-md.md)]関数またはメソッドです。  
  
-   直接または間接的にアセンブリ内のメソッドを参照する、CHECK 制約。  
  
-   アセンブリと型を実装に依存する CLR ユーザー定義型の列、 **UserDefined** (非**ネイティブ**) シリアル化形式。  
  
-   WITH SCHEMABINDING を使用して作成されたビューを参照する、CLR ユーザー定義型の列。  
  
 CHECK 制約がある場合、これらのデータは無効になり、信頼されていないことを示すマークが付きます。 アセンブリに依存する列が含まれるテーブルは、明示的に検証されるまで、未検証のデータが含まれていることを示すマークが付きます。  
  
 メンバーにのみ、 **db_owner**と**db_ddlowner**固定データベース ロールは、このオプションを指定できます。  
  
 必要があります、 **ALTER ANY SCHEMA**アクセス許可をこのオプションを指定します。  
  
 詳細については、次を参照してください。[を実装するアセンブリ](../../relational-databases/clr-integration/assemblies-implementing.md)です。  
  
 [DROP FILE { *file_name*[ **、***...n*] |ALL}]  
 アセンブリに関連付けられているファイル名、またはアセンブリに関連付けられているすべてのファイルを、データベースから削除します。 続けて ADD FILE を指定する場合は、最初に DROP FILE が実行されます。 このため、同じファイル名でファイルを置き換えることができます。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
 [ADD FILE FROM { *client_file_specifier* [AS *file_name*] |*file_bits*AS *file_name*}  
 デバッグ ファイルをソース コードなど、アセンブリに関連付けられているファイルをアップロードや他の関連サーバーへの情報に表示される、 **sys.assembly_files**カタログ ビューです。 *client_file_specifier*ファイルをアップロードする場所を指定します。 *file_bits*ファイルを構成するバイナリ値の一覧を指定する代わりに使用されることができます。 *file_name*のインスタンスにするファイルを保存するか名前を示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 *file_name*場合に指定する必要があります*file_bits*を指定すると、省略可能な場合は*client_file_specifier*を指定します。 場合*file_name*が指定されていないの file_name 部分*client_file_specifier*として使用される*file_name*です。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
## <a name="remarks"></a>解説  
 変更するアセンブリ内のコードが、現在実行中のセッションで実行されている場合、ALTER ASSEMBLY でセッションは中断されません。 現在のセッションは、アセンブリの変更されていないビット列を使用して最後まで実行されます。  
  
 FROM 句を指定した場合、ALTER ASSEMBLY では、指定したモジュールの最新コピーが反映されるようにアセンブリが更新されます。 CLR 関数、ストアド プロシージャ、トリガー、データ型、およびユーザー定義の集計関数のインスタンスがある可能性があるため[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アセンブリに対して既に定義されている、ALTER ASSEMBLY ステートメントを再バインド最新アセンブリの実装です。 この再バインドを適切に行うには、CLR 関数、ストアド プロシージャ、およびトリガーにマップされるメソッドが、同じ署名を持つ変更済みのアセンブリ内に存在している必要があります。 CLR ユーザー定義型とユーザー定義集計関数が実装されているクラスは、ユーザー定義型または集計の要件を満たしている必要があります。  
  
> [!CAUTION]  
>  WITH UNCHECKED DATA を指定しない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ALTER ASSEMBLY がアセンブリの新しいバージョンのテーブル、インデックス、またはその他の永続的なサイトの既存のデータに影響を実行することを防止しようとしています。 ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]計算列、インデックス、インデックス付きビュー、または CLR アセンブリが更新されたときに、式が、基になるルーチンおよびデータ型と一致することは保証されません。 式の結果と、アセンブリに格納されている式に基づく値に不一致がないかどうかを ALTER ASSEMBLY で確認する場合は注意してください。  
  
 ALTER ASSEMBLY ではアセンブリのバージョンが変更されます。 アセンブリのカルチャおよび公開キー トークンは変更されません。  
  
 ALTER ASSEMBLY ステートメントを使用しても、次の情報は変更できません。  
  
-   アセンブリを参照する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内の CLR 関数、集計関数、ストアド プロシージャ、およびトリガーの署名。 ALTER ASSEMBLY が失敗したときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]再バインドできない[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]内のデータベース オブジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アセンブリの新しいバージョンです。  
  
-   別のアセンブリから呼び出されるアセンブリ内のメソッドの署名。  
  
-   参照されているとおりのアセンブリに依存するアセンブリの一覧、 **DependentList**アセンブリのプロパティです。  
  
-   メソッドのインデックス機能。ただし、直接または間接的にそのメソッドに依存するインデックスや保存される計算列が存在する場合に限ります。  
  
-   **FillRow**メソッド名 CLR テーブル値関数の属性です。  
  
-   **Accumulate**と**Terminate**ユーザー定義集計のメソッドの署名。  
  
-   システム アセンブリ。  
  
-   アセンブリの所有権。 使用して[ALTER AUTHORIZATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-authorization-transact-sql.md)代わりにします。  
  
 さらに、ユーザー定義型を実装するアセンブリに対しては、ALTER ASSEMBLY を使用して次の変更だけを行えます。  
  
-   ユーザー定義型クラスのパブリック メソッドの変更 (署名または属性が変更されない場合のみ)。  
  
-   新しいパブリック メソッドの追加。  
  
-   プライベート メソッドの変更。  
  
 データ メンバーやベース クラスなど、ネイティブでシリアル化されたユーザー定義型に含まれるフィールドは、ALTER ASSEMBLY では変更できません。 その他すべての変更はサポートされていません。  
  
 ADD FILE FROM を指定しない場合、ALTER ASSEMBLY ではそのアセンブリに関連付けられているファイルが削除されます。  
  
 UNCHECKED データ句を指定せずに ALTER ASSEMBLY を実行した場合は、新しいバージョンのアセンブリがテーブル内の既存のデータに影響しないかどうかを検証するためのチェックが行われます。 チェックの対象となるデータ量によっては、パフォーマンスが影響を受ける場合があります。  
  
## <a name="permissions"></a>Permissions  
 アセンブリに対する ALTER 権限が必要です。 その他、次の追加要件があります。  
  
-   アセンブリが既存のアクセス許可を変更するセットが EXTERNAL_ACCESS は、必要があります**EXTERNAL ACCESS ASSEMBLY**サーバーに対する権限。  
  
-   セットが UNSAFE をアセンブリが既存のアクセス許可を変更する必要があります**UNSAFE ASSEMBLY**サーバーに対する権限。  
  
-   EXTERNAL_ACCESS にアセンブリの権限のセットを変更する必要があります**EXTERNAL ACCESS ASSEMBLY**サーバーに対する権限。  
  
-   UNSAFE アセンブリの権限のセットを変更する必要があります。 **UNSAFE ASSEMBLY**サーバーに対する権限。  
  
-   指定する WITH UNCHECKED DATA を必要と**ALTER ANY SCHEMA**権限です。  


### <a name="permissions-with-clr-strict-security"></a>CLR の厳格なセキュリティ アクセス許可    
CLR アセンブリを変更するために必要な次のアクセス許可と`CLR strict security`が有効になっています。

- ユーザーには `ALTER ASSEMBLY` アクセス許可が必要です  
- さらに、次の条件のいずれかを満たす必要があります。  
  - サーバーでの `UNSAFE ASSEMBLY` アクセス許可のある対応するログインを含む証明書または非対称キーでアセンブリが署名されている。 アセンブリへの署名は推奨されます。  
  - データベースに `ON` に設定された `TRUSTWORTHY` プロパティが含まれ、そのデータベースがサーバーでの `UNSAFE ASSEMBLY` アクセス許可のあるログインによって所有されている。 このオプションは推奨されません。  
  
  
 アセンブリの権限セットの詳細については、次を参照してください。[アセンブリの設計](../../relational-databases/clr-integration/assemblies-designing.md)です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-refreshing-an-assembly"></a>A. アセンブリを更新する  
 次の例では、`ComplexNumber` アセンブリを更新して、その実装を保持する [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] モジュールの最新コピーを反映させます。  
  
> [!NOTE]  
>  アセンブリ `ComplexNumber` は、サンプル スクリプト UserDefinedDataType を実行することによって作成できます。 詳細については、次を参照してください。[ユーザー定義型](http://msdn.microsoft.com/library/a9b75f36-d7f5-47f7-94d6-b4448c6a2191)です。  
  
 `ALTER ASSEMBLY ComplexNumber`  
  
 `FROM 'C:\Program Files\Microsoft SQL Server\130\Tools\Samples\1033\Engine\Programmability\CLR\UserDefinedDataType\CS\ComplexNumber\obj\Debug\ComplexNumber.dll'`  
  
### <a name="b-adding-a-file-to-associate-with-an-assembly"></a>B. ファイルを追加してアセンブリに関連付ける  
 次の例は、ソース コード ファイルをアップロード`Class1.cs`アセンブリに関連付ける`MyClass`です。 この例では、アセンブリ `MyClass` がデータベースに既に作成されていることを前提としています。  
  
```  
ALTER ASSEMBLY MyClass   
ADD FILE FROM 'C:\MyClassProject\Class1.cs';  
```  
  
### <a name="c-changing-the-permissions-of-an-assembly"></a>C. アセンブリの権限を変更する  
 次の例では、アセンブリ `ComplexNumber` の権限セットを、SAFE から `EXTERNAL ACCESS` に変更します。  
  
```  
ALTER ASSEMBLY ComplexNumber WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
## <a name="see-also"></a>参照  
 [アセンブリ &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-assembly-transact-sql.md)   
 [アセンブリ &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-assembly-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

