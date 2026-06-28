# NARC for the in-battle Pokemon party list (bottom screen).
# Registered in code as NARC_INDEX_BATTLE__GRAPHIC__PL_B_PLIST_GRA and mapped to
# the NitroFS path /battle/graphic/pl_b_plist_gra.narc via platinum.us/filesys.csv.
#
# Member layout (see party_list.order). Members 0-21 are screen-layout tilemaps
# referenced by index in ScreenBackgroundDataMemberIndexes
# (src/battle_sub_menus/battle_party.c). Members 22-27 are the shared BG/OBJ
# graphics resources loaded in battle_party.c / battle_party_sprites.c:
#   22 -> BG tiles      (plist_bg_tiles.png)
#   23 -> BG palette    (plist_bg.pal)
#   24 -> OBJ animation (plist_obj_anim.json)
#   25 -> OBJ cell      (plist_obj_cell.json)
#   26 -> OBJ tiles     (plist_obj_tiles.png)
#   27 -> OBJ palette   (plist_obj.pal)
party_list_narc = custom_target('pl_b_plist_gra.narc',
    output: [
        'pl_b_plist_gra.narc',
        'pl_b_plist_gra.naix.h',
    ],

    input: [
        copy_gen.process(
            files(
                'plist_bg_00.NSCR',
                'plist_bg_01.NSCR',
                'plist_bg_02.NSCR',
                'plist_bg_03.NSCR',
                'plist_bg_04.NSCR',
                'plist_bg_05.NSCR',
                'plist_bg_06.NSCR',
                'plist_bg_07.NSCR',
                'plist_bg_08.NSCR',
                'plist_bg_09.NSCR',
                'plist_bg_10.NSCR',
                'plist_bg_11.NSCR',
                'plist_bg_12.NSCR',
                'plist_bg_13.NSCR',
                'plist_bg_14.NSCR',
                'plist_bg_15.NSCR',
                'plist_bg_16.NSCR',
                'plist_bg_17.NSCR',
                'plist_bg_18.NSCR',
                'plist_bg_19.NSCR',
                'plist_bg_20.NSCR',
                'plist_bg_21.NSCR',
            )
        ),
        ncgr_gen.process(
            files('plist_bg_tiles.png'),
            extra_args: ['-version101', '-sopc'],
        ),
        ncgr_gen.process(
            files('plist_obj_tiles.png'),
            extra_args: ['-version101', '-clobbersize'],
        ),
        nclr_gen.process(
            files(
                'plist_bg.pal',
                'plist_obj.pal',
            ),
            extra_args: ['-bitdepth', '4'],
        ),
        ncer_gen.process(
            files('plist_obj_cell.json')
        ),
        nanr_gen.process(
            files('plist_obj_anim.json')
        ),
    ],

    command: [
        narc_exe, 'create', '--naix',
        '--order', files('party_list.order'),
        '--output', '@OUTPUT0@',
        '@PRIVATE_DIR@',
    ]
)

nitrofs_files += party_list_narc
naix_headers += party_list_narc[1]
