---
title: CLR 統合プログラミング モデルの制限事項 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 039afe6cbe5892d2422eec3c92a4d2bb942d5de0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072813"
---
# <a name="clr-integration-programming-model-restrictions"></a>CLR 統合プログラミング モデルの制限事項
  マネージ ストアド プロシージャやその他のマネージ データベース オブジェクトを作成するときはコードのチェックが実行される特定の[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]最初に、データベースに登録されているときに、マネージ コード アセンブリに対する検査は実行を使用して、 `CREATE ASSEMBLY`ステートメント、および実行時にもします。 マネージ コードが実行時にもチェックされるのは、実行時に決して到達しないコード パスがアセンブリに含まれる場合があるためです。  このチェックにより、サード パーティ アセンブリを柔軟に登録できます。特に、クライアント環境での実行を目的に作成され、ホストされた CLR では実行されない "安全でない" コードを含むアセンブリをブロックしないようにすることができるため、サード パーティ アセンブリに柔軟に対応できます。 マネージ コードが満たす必要がある要件として、アセンブリが登録されているかどうかによって変わります`SAFE`、 `EXTERNAL_ACCESS`、または`UNSAFE`、`SAFE`最も制限の厳しい、され、次のとおりです。  
  
 マネージ コード アセンブリには、制限事項に加えてコード セキュリティ権限も付与されます。 共通言語ランタイム (CLR) では、マネージ コードに対してコード アクセス セキュリティ (CAS) というセキュリティ モデルがサポートされます。 このモデルでは、コードの ID に基づいてアセンブリに権限が許可されます。 `SAFE`、`EXTERNAL_ACCESS`、および `UNSAFE` の各アセンブリには、それぞれ異なる CAS 権限が付与されます。 詳細については、次を参照してください。 [CLR 統合のコード アクセス セキュリティ](../security/clr-integration-code-access-security.md)です。  
  
## <a name="create-assembly-checks"></a>CREATE ASSEMBLY チェック  
 `CREATE ASSEMBLY` ステートメントを実行する際には、セキュリティ レベルごとに次のチェックが実行されます。  いずれかのチェックが失敗した場合、`CREATE ASSEMBLY` が失敗し、エラー メッセージが表示されます。  
  
### <a name="global-any-security-level"></a>グローバル (すべてのセキュリティ レベル)  
 参照されるすべてのアセンブリは、次の条件のうち 1 つ以上を満たす必要があります。  
  
-   既にデータベースに登録されていること。  
  
-   サポートされているアセンブリの 1 つであること。 詳細については、次を参照してください。[サポートされている .NET Framework ライブラリ](supported-net-framework-libraries.md)です。  
  
-   使用している`CREATE ASSEMBLY FROM` *\<場所 >、* すべての参照先アセンブリとその依存関係がで利用できる*\<場所 >* です。  
  
-   使用している`CREATE ASSEMBLY FROM` *\<バイト... >、* 参照が領域を使用して指定されたすべての区切りのバイトとします。  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 すべての `EXTERNAL_ACCESS` アセンブリは、次の条件を満たす必要があります。  
  
-   静的フィールドが情報の格納に使用されていないこと。 読み取り専用の静的フィールドは許可されます。  
  
-   PEVerify テストにパスしていること。 .NET Framework SDK には、MSIL コードと関連メタデータがタイプ セーフの要件を満たしていることをチェックするための PEVerify ツール (peverify.exe) が付属しています。  
  
-   `SynchronizationAttribute` クラスなどによる同期が使用されていないこと。  
  
-   ファイナライザー メソッドが使用されていないこと。  
  
 `EXTERNAL_ACCESS` アセンブリでは、次のカスタム属性が許可されません。  
  
-   System.ContextStaticAttribute  
  
-   System.MTAThreadAttribute  
  
-   System.Runtime.CompilerServices.MethodImplAttribute  
  
-   System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
  
-   System.Runtime.Remoting.Contexts.ContextAttribute  
  
-   System.Runtime.Remoting.Contexts.SynchronizationAttribute  
  
-   System.Runtime.InteropServices.DllImportAttribute  
  
-   System.Security.Permissions.CodeAccessSecurityAttribute  
  
-   System.Security.SuppressUnmanagedCodeSecurityAttribute  
  
-   System.Security.UnverifiableCodeAttribute  
  
-   System.STAThreadAttribute  
  
-   System.ThreadStaticAttribute  
  
### <a name="safe"></a>SAFE  
  
-   `EXTERNAL_ACCESS` アセンブリの条件がすべてチェックされていること。  
  
## <a name="runtime-checks"></a>ランタイム チェック  
 コード アセンブリは、実行時に次の条件をチェックされます。 これらの条件のいずれかが見つからなかった場合、マネージ コードの実行が失敗し、例外がスローされます。  
  
### <a name="unsafe"></a>UNSAFE  
 `System.Reflection.Assembly.Load()` メソッドの呼び出しによるバイト列からのアセンブリの明示的な読み込み、および `Reflection.Emit` 名前空間を使用したアセンブリの暗黙的な読み込みは許可されません。  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 `UNSAFE` の条件がすべてチェックされていること。  
  
 サポートされているアセンブリの一覧の中で、次のホスト保護属性 (HPA) 値で注釈を付けられている型およびメンバーはすべて許可されません。  
  
-   SelfAffectingProcessMgmt  
  
-   SelfAffectingThreading  
  
-   Synchronization  
  
-   SharedState  
  
-   ExternalProcessMgmt  
  
-   ExternalThreading  
  
-   SecurityInfrastructure  
  
-   MayLeakOnAbort  
  
-   UI  
  
 Hpa およびサポートされているアセンブリの許可されない型およびメンバーの一覧の詳細については、次を参照してください。[ホスト保護属性と CLR 統合プログラミング](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)です。  
  
### <a name="safe"></a>SAFE  
 `EXTERNAL_ACCESS` の条件がすべてチェックされていること。  
  
## <a name="see-also"></a>参照  
 [サポートされている .NET Framework ライブラリ](supported-net-framework-libraries.md)   
 [CLR 統合のコード アクセス セキュリティ](../security/clr-integration-code-access-security.md)   
 [ホスト保護属性と CLR 統合プログラミング](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [アセンブリの作成](../assemblies/creating-an-assembly.md)  
  
  