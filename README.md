# Versioning library for generating next stable version number

Doing continuous deployment from a green branch is recommended to do
using PyPI packages. Creating these packages can be done using
setuptools, but bumping the version while complying with version
naming conventions can be tedious. This library helps automate it.

It will look up the latest version available in the repository, then
bump to the nearest next version. E.G 1.5.3 -> 1.5.4

To ensure compatibility with any custom PyPI repositories, it's using
pip from command line.

## Example usage

    #!/usr/bin/env python
    from packageversion import PackageVersion
    from setuptools import setup, find_packages
    
    pv = PackageVersion()
    v = pv.generate_next_stable(package_name='packageversion')
    
    setup(name='packageversion',
          version=v,
          description='Library to generate python package version for CI',
          author='Jon Skarpeteig',
          author_email='jon.skarpeteig@gmail.com',
          url='https://github.com/Yuav/python-packageversion',
          packages=find_packages(),
          install_requires=[
              'semantic_version',
              'flexmock'
          ]
          )
          
## Known issues

 - Requires pip > 1.0 since output syntax for versions is broken in 1.0
 - Requires python3