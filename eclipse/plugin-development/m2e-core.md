
代码阅读：

入口1 新建Maven工程 MavenProjectWizard 
                    PAGES: MavenProjectWizardLocationPage //路径
                        
        Simple Project: -> MavenProjectWizardArtifactPage  //直接基于group id, artifact id 等信息新建Maven库 
      Archetype Project -> MavenProjectWizardArchetypePage //已有的Archetype列表
                        -> MavenProjectWizardArchetypeParametersPage //添加额外的参数

入口2 新建Maven模块 MavenModuleWizard 
                    Pages: MavenModuleWizardParentPage  //选择模块
			-> MavenProjectWizardArchetypePage 
                        -> MavenProjectWizardArtifactPage
                        -> MavenProjectWizardArchetypeParametersPage



AbstractCreateMavenProjectJob


DefaultArchetypeManager  ArchetypeGenerator（DefaultArchetypeGenerator） 
                          OldArchetype      (DefaultOldArchetype)
                          ArchetypeDescriptorBuilder（）
                         ArchetypeDescriptor (Archetype 描述文件)

context <VelocityContext>
{basedir=/home/zheng/runtime-EclipseApplication, package=qww.asd, groupId=qww, artifactId=asd, packageName=qww.asd, version=0.0.1-SNAPSHOT}




