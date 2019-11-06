---
title: アセンブリを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- creating assemblies
- UNSAFE assemblies
- CREATE ASSEMBLY statement
- SAFE assemblies
- EXTERNAL_ACCESS assemblies
- assemblies [CLR integration], creating
ms.assetid: a2bc503d-b6b2-4963-8beb-c11c323f18e0
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e28871e93bd718063692a31a4a3462399517dfc9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62919573"
---
# <a name="creating-an-assembly"></a>アセンブリの作成
  ストアド プロシージャやトリガーなどのマネージド データベース オブジェクトは、コンパイルされた後、アセンブリと呼ばれる単位で配置されます。 マネージ DLL アセンブリを登録する必要があります[!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)]アセンブリが提供する機能を使用する前にします。 アセンブリを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに登録するには、CREATE ASSEMBLY ステートメントを使用します。 ここでは、CREATE ASSEMBLY ステートメントを使用してアセンブリをデータベースに登録する方法と、アセンブリのセキュリティ設定を指定する方法について説明します。  
  
## <a name="the-create-assembly-statement"></a>CREATE ASSEMBLY ステートメント  
 データベースにアセンブリを作成するには、CREATE ASSEMBLY ステートメントを使用します。 以下に例を示します。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 FROM 句では、作成するアセンブリのパス名を指定します。 このパスには、UNC (汎用名前付け規則) パスか、コンピューターにローカルの物理ファイル パスを指定できます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、名前、カルチャ、および公開キーが同じでありバージョンが異なるアセンブリの登録を許可していません。  
  
 他のアセンブリを参照するアセンブリを作成することもできます。 アセンブリを作成するときに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]参照アセンブリが既にデータベースに作成されない場合も、ルート レベル アセンブリによって参照されるアセンブリを作成します。  
  
 データベース ユーザーまたはユーザー ロールには、データベースにアセンブリを作成して所有する権限が与えられます。 アセンブリを作成するには、データベース ユーザーまたはロールに CREATE ASSEMBLY 権限が許可されている必要があります。  
  
 アセンブリから他のアセンブリを参照できる条件を次に示します。  
  
-   呼び出し先または参照先のアセンブリが同じユーザーまたはロールによって所有されている。  
  
-   呼び出し先または参照先のアセンブリが同じデータベースに作成されている。  
  
## <a name="specifying-security-when-creating-assemblies"></a>アセンブリ作成時のセキュリティの指定  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースにアセンブリを作成する際には、コードの実行時に適用する異なる 3 つのセキュリティ レベル (`SAFE`、`EXTERNAL_ACCESS`、`UNSAFE`) のうちの 1 つを指定できます。 `CREATE ASSEMBLY` ステートメントを実行する際には、アセンブリによる登録を失敗させる可能性があるコード アセンブリに対し、特定のチェックがサーバー上で実行されます。 詳細については、の Impersonation サンプルを参照してください。 [CodePlex](http://msftengprodsamples.codeplex.com/)します。  
  
 `SAFE` は、ほとんどのシナリオに使用できる既定の権限セットです。 特定のセキュリティ レベルを指定するには、CREATE ASSEMBLY ステートメントの構文を次のように変更します。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 上記のコードの 3 行目を省略しても、`SAFE` 権限セットを持つアセンブリを作成できます。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 `SAFE` 権限セットで実行されるアセンブリ内のコードでは、インプロセス マネージド プロバイダーを経由して、計算とサーバーのデータへのアクセスのみを実行できます。  
  
### <a name="creating-externalaccess-and-unsafe-assemblies"></a>EXTERNAL_ACCESS および UNSAFE アセンブリの作成  
 `EXTERNAL_ACCESS` は、ファイル、ネットワーク、レジストリ、環境変数など、サーバー外部のリソースにコードからアクセスする必要がある場合に使用します。 サーバーから外部リソースにアクセスする場合、常にマネージド コードの呼び出し元のユーザーのセキュリティ コンテキストが借用されます。  
  
 `UNSAFE` コード権限は、アセンブリが安全であると検証できない場合や、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 API などの制限付きのリソースへの追加アクセスが必要な場合に使用します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で `EXTERNAL_ACCESS` または `UNSAFE` アセンブリを作成するには、次の 2 つの条件のいずれかが満たされている必要があります。  
  
1.  アセンブリが、厳密な名前で署名されているか、または証明書を使用して Authenticode で署名されている。 この厳密な名前 (または証明書) は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 内部で非対称キー (または証明書) として作成され、それに対応する、`EXTERNAL ACCESS ASSEMBLY` 権限 (外部アクセス アセンブリの場合) または `UNSAFE ASSEMBLY` 権限 (安全でないアセンブリの場合) を持つログインが存在します。  
  
2.  データベース所有者 (DBO) が`EXTERNAL ACCESS ASSEMBLY`(の`EXTERNAL ACCESS`アセンブリ) または`UNSAFE ASSEMBLY`(の`UNSAFE`アセンブリ) アクセス許可、およびデータベースが、 [TRUSTWORTHY データベース プロパティ](../../security/trustworthy-database-property.md)設定`ON`します。  
  
 上に示した 2 つの条件は、アセンブリの読み込み時 (実行も含む) にもチェックされます。 アセンブリを読み込むには、これらの条件の少なくとも 1 つが満たされている必要があります。  
  
 お勧め、 [TRUSTWORTHY データベース プロパティ](../../security/trustworthy-database-property.md)データベースでないに設定する`ON`ランタイム (CLR) がサーバー プロセス内のコードに共通の言語を実行するだけです。 代わりに、master データベースのアセンブリ ファイルから非対称キーを作成してください。 その場合、この非対称キーにマップされるログインを作成する必要があります。また、このログインには、`EXTERNAL ACCESS ASSEMBLY` または `UNSAFE ASSEMBLY` 権限を与える必要があります。  
  
 次[!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメント、CREATE ASSEMBLY ステートメントを実行する前にします。  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll'     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey     
GRANT EXTERNAL ACCESS ASSEMBLY TO SQLCLRTestLogin;   
GO   
```  
  
> [!NOTE]  
>  非対称キーに関連付ける新しいログインを作成する必要があります。 このログインは、権限を許可するためにのみ使用します。このログインをユーザーに関連付けたり、アプリケーション内で使用したりする必要はありません。  
  
 `EXTERNAL ACCESS` アセンブリを作成するには、作成者に `EXTERNAL ACCESS` 権限が許可されている必要があります。 この権限は、アセンブリの作成時に次のように指定します。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 次[!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメント、CREATE ASSEMBLY ステートメントを実行する前にします。  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 アセンブリを `UNSAFE` 権限で読み込むには、そのアセンブリをサーバーに読み込むときに、次のように `UNSAFE` 権限セットを指定します。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 各設定のアクセス許可の詳細については、次を参照してください。 [CLR 統合セキュリティ](../security/clr-integration-security.md)します。  
  
## <a name="see-also"></a>参照  
 [CLR 統合アセンブリの管理](managing-clr-integration-assemblies.md)   
 [アセンブリの変更](altering-an-assembly.md)   
 [アセンブリの削除](dropping-an-assembly.md)   
 [CLR 統合のコード アクセス セキュリティ](../security/clr-integration-code-access-security.md)   
 [TRUSTWORTHY データベース プロパティ](../../security/trustworthy-database-property.md)   
 [部分的に信頼される呼び出し元の許容](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
  
  
