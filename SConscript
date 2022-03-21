from building import *

cwd  = GetCurrentDir()
CPPPATH = [cwd]

src = ['qrcode.c']

if GetDepend(['PKG_QRCODE_SAMPLE']):
    src += ['qrcode_sample.c']

group = DefineGroup('qrcode', src, depend = ['PKG_USING_QRCODE'], CPPPATH = CPPPATH)

Return('group')
